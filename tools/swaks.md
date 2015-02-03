# swaks

Notes
-------

Help Text
-------
Help file just points to the man page
```SWAKS(1)                             SWAKS                            SWAKS(1)



NAME
       swaks - Swiss Army Knife SMTP, the all-purpose smtp transaction tester

DESCRIPTION
       swaks' primary design goal is to be a flexible, scriptable,
       transaction-oriented SMTP test tool.  It handles SMTP features and
       extensions such as TLS, authentication, and pipelining; multiple
       version of the SMTP protocol including SMTP, ESMTP, and LMTP; and
       multiple transport methods including unix-domain sockets, internet-
       domain sockets, and pipes to spawned processes.  Options can be
       specified in environment variables, configuration files, and the
       command line allowing maximum configurability and ease of use for
       operators and scripters.

QUICK START
       Deliver a standard test email to user@example.com on port 25 of
       test-server.example.net:

        swaks --to user@example.com --server test-server.example.net

       Deliver a standard test email, requiring CRAM-MD5 authentication as
       user me@example.com.  An "X-Test" header will be added to the email
       body.  The authentication password will be prompted for.

        swaks --to user@example.com --from me@example.com --auth CRAM-MD5 --auth-user me@example.com --header-X-Test "test email"

       Test a virus scanner using EICAR in an attachment.  Don't show the
       message DATA part.:

        swaks -t user@example.com --attach - --server test-server.example.com --suppress-data </path/to/eicar.txt

       Test a spam scanner using GTUBE in the body of an email, routed via the
       MX records for example.com:

        swaks --to user@example.com --body /path/to/gtube/file

       Deliver a standard test email to user@example.com using the LMTP
       protocol via a UNIX domain socket file

        swaks --to user@example.com --socket /var/lda.sock --protocol LMTP

       Report all the recipients in a text file that are non-verifyiable on a
       test server:

        for E in `cat /path/to/email/file`
        do
            swaks --to $E --server test-server.example.com --quit-after RCPT --hide-all
            [ $? -ne 0 ] && echo $E
        done

TERMS AND CONVENTIONS
       This document tries to be consistent and specific in its use of the
       following terms to reduce confusion.

       Transaction
           A transaction is the opening of a connection over a transport to a
           target and using a messaging protocol to attempt to deliver a
           message.

       Target
           The target of a transaction is the thing that swaks connects to.
           This generic term is used throughout the documentation because most
           other terms improperly imply something about the transport being
           used.

       Transport
           The transport is the underlying method used to connect to the
           target.

       Protocol
           The protocol is the application language used to communicate with
           the target.  This document uses SMTP to speak generically of all
           three supported protocols unless it states that it is speaking of
           the specific 'SMTP' protocol and excluding the others.

       Message
           SMTP protocols exist to transfer messages, a set of bytes in an
           agreed-upon format that has a sender and a recipient.

       Envelope
           A message's envelope contains the "true" sender and receiver of a
           message.  It can also be referred to as its components, envelope-
           sender and envelope-recipients.  It is important to note that a
           messages envelope does not have to match its To: and From: headers.

       DATA
           The DATA portion of an SMTP transaction is the actual message that
           is being transported.  It consists of both the message's headers
           and its body.  DATA and body are sometimes use synonymously, but
           they are always two distinct things in this document.

       Headers
           A message's headers are defined as all the lines in the message's
           DATA section before the first blank line.  They contain information
           about the email that will be displayed to the recipient such as
           To:, From:, Subject:, etc.  In this document headers will always be
           written with a capitalized first letter and a trailing colon.

       Body
           A message's body is the portion of its DATA section following the
           first blank line.

OPTION PROCESSING
       To prevent potential confusion in this document a flag to swaks is
       always referred to as an "option".  If the option takes additional
       data, that additional data is referred to as an argument to the option.
       For example, "--from fred@example.com" might be provided to swaks on
       the command line, with "--from" being the option and "fred@example.com"
       being --from's argument.

       Options can be given to swaks in three ways.  They can be specified in
       a configuration file, in environment variables, and on the command
       line.  Depending on the specific option and whether or not an argument
       is given to it, swaks may prompt the user for the argument.

       When swaks evaluates its options, it first looks for a configuration
       file (either in a default location or specified with --config).  Then
       it evaluates any options in environment variables.  Finally, it
       evaluates command line options.  At each round of processing, any
       options set earlier will be overridden.  Additionally, any option can
       be prefixed with "no-" to cause swaks to forget that the variable had
       previously been set.  This capability is necessary because many options
       treat defined-but-no-argument differently than not-defined.

       The exact mechanism and format for using each of the types is listed
       below.

       CONFIGURATION FILE
           A configuration file can be used to set commonly-used or abnormally
           verbose options.  By default swaks looks in order for
           $SWAKS_HOME/.swaksrc, $HOME/.swaksrc, and $LOGDIR/.swaksrc.  If one
           of those is found to exist (and --config has not been used) that
           file is used as the configuration file.

           Additionally a configuration file in a non-default location can be
           specified using --config.  If this is set and not given an argument
           swaks will not use any configuration file, including any default
           file.  If --config points to a readable file, it is used as the
           configuration file, overriding any default that may exist.  If it
           points to a non-readable file and error will be shown and swaks
           will exit.

           A set of "portable" defaults can also be created by adding options
           to the end of the swaks program file.  As distributed, the last
           line of swaks should be "__END__".  Any lines added after __END__
           will be treated as the contents of a configuration file.  This
           allows a set of user preferences to be automatically copied from
           server to server in a single file.

           If present and configuration files have not been explicitly turned
           off, the __END__ config is always read.  Only one other
           configuration file will ever be used per single invocation of
           swaks, even if multiple configuration files are specified.
           Specifying the --config option with no argument turns off the
           processing of both the __END__ config and any actual config files.

           In a configuration file lines beginning with a hash (#) are
           ignored.  All other lines are assumed to be an option to swaks,
           with the leading dash or dashes optional.  Everything after a
           option line's first space is assumed to be the option's argument
           and is not shell processed.  Therefore quoting is usually unneeded
           and will be included literally in the argument.  Here is an example
           of the contents of a configuration file:

               # always use this sender, no matter server or logged in user
               --from fred@example.com
               # I prefer my test emails have a pretty from header.  Note
               # the lack of dashes on option and lack of quotes around
               # entire argument.
               h-From: "Fred Example" <fred@example.com>

       ENVIRONMENT VARIABLES
           Options can be supplied via environment variables.  The variables
           are in the form $SWAKS_OPT_name, where name is the name of the
           option that would be specified on the command line.  Because dashes
           aren't allowed in environment variable names in most unix-ish
           shells, no leading dashes should be used and any dashes inside the
           option's name should be replaced with underscores.  The following
           would create the same options shown in the configuration file
           example:

               $ SWAKS_OPT_from='fred@example.com'
               $ SWAKS_OPT_h_From='"Fred Example" <fred@example.com>'

           Setting a variable to an empty value is the same as specifying it
           on the command line with no argument.  For instance, setting
           SWAKS_OPT_server="" would cause swaks to prompt the use for the
           server to which to connect at each invocation.

           In addition to setting the equivalent of command line options,
           SWAKS_HOME can be set to a directory containing the default
           .swaksrc to be used.

       COMMAND LINE OPTIONS
           The final method of supplying options to swaks is via the command
           line.  The options behave in a manner consistent with most unix-ish
           command line programs.  Many options have both a short and long
           form (for instance -s and --server).  By convention short options
           are specified with a single dash and long options are specified
           with a double-dash.  This is only a convention and either prefix
           will work with either type.

           The following demonstrates the example shown in the configuration
           file and environment variable sections:

               $ swaks --from fred@example.com --h-From: '"Fred Example" <fred@example.com>'

TRANSPORTS
       swaks can connect to a target via unix pipes ("pipes"), unix domain
       sockets ("unix sockets"), or internet domain sockets ("network
       sockets").  Connecting via network sockets is the default behavior.
       Because of the singular nature of the transport used, each set of
       options in the following section is mutually exclusive.  Specifying
       more than one of --server, --pipe, or --socket will result in an error.
       Mixing other options between transport types will only result in the
       irrelevant options being ignored.  Below is a brief description of each
       type of transport and the options that are specific to that transport
       type.

       NETWORK SOCKETS
           This transport attempts to deliver a message via TCP/IP, the
           standard method for delivering SMTP.  This is the default transport
           for swaks.  If none of --server, --pipe, or --socket are given then
           this transport is used and the target server is determined from the
           recipient's domain (see --server below for more details).

           This transport requires the IO::Socket module which is part of the
           standard perl distribution.  If this module is not loadable,
           attempting to use a this transport will result in an error and
           program termination.

           IPv6 is supported when the IO::Socket::INET6 module is present.

           -s, --server [target mail server[:port]]
               Explicitly tell swaks to use network sockets and specify the
               hostname or IP address to which to connect, or prompt if no
               argument is given.  If this option is not given and no other
               transport option is given, the target mail server is determined
               from the appropriate DNS records for the domain of the
               recipient email address using the Net::DNS module.  If Net::DNS
               is not available swaks will attempt to connect to localhost to
               deliver.  The target port can optionally be set here.
               Supported formats for this include SERVER:PORT (supporting
               names and IPv4 addresses); [SERVER]:PORT and SERVER/PORT
               (supporting names, IPv4 and IPv6 addresses).  See also
               --copy-routing.

           -p, --port [port]
               Specify which TCP port on the target is to be used, or prompt
               if no argument is listed.  The argument can be a service name
               (as retrieved by getservbyname(3)) or a port number.  The
               default port is determined by the --protocol option.  See
               --protocol for more details.

           -li, --local-interface [IP or hostname[:port]]
               Use argument as the local interface for the outgoing SMTP
               connection, or prompt user if no argument given.  Argument can
               be an IP address or a hostname.  Default action is to let the
               operating system choose local interface.  See --server for
               additional comments on :port format.

           -lp, --local-port [port]
               Specify the outgoing port to originate the transaction from.
               If this option is not specified the system will pick an
               ephemeral port.  Note that regular users cannot specify some
               ports.

           --copy-routing [domain]
               The argument is interpreted as the domain part of an email
               address and it is used to find the target server using the same
               logic that would be used to look up the target server for an
               recipient email address.  See  --to option for more details on
               how the target is determined from the email domain.

           -4, -6
               Force IPv4 or IPv6.

       UNIX SOCKETS
           This transport method attempts to deliver messages via a unix-
           domain socket file.  This is useful for testing MTA/MDAs that
           listen on socket files (for instance, testing LMTP delivery to
           Cyrus).  This transport requires the IO::Socket module which is
           part of the standard perl distribution.  If this module is not
           loadable, attempting to use this transport will result in an error
           and program termination.

           --socket [/path/to/socket/file]
               This option takes as its argument a unix-domain socket file.
               If swaks is unable to open this socket it will display an error
               and exit.

       PIPES
           This transport attempts to spawn a process and communicate with it
           via pipes.  The spawned program must be prepared to behave as a
           mail server over STDIN/STDOUT.  Any MTA designed to operate from
           inet/xinet should support this.  In addition some MTAs provide
           testing modes that can be communicated with via STDIN/STDOUT.  This
           transport can be used to automate that testing.  For example, if
           you implemented DNSBL checking with Exim and you wanted to make
           sure it was working, you could run 'swaks --pipe "exim -bh
           127.0.0.2"'.  In an ideal world the process you are talking to
           should behave exactly like an SMTP server on stdin and stdout.  Any
           debugging should be sent to stderr, which will be directed to your
           terminal.  In the real world swaks can generally handle some debug
           on the child's stdout, but there are no guarantees on how much it
           can handle.

           This transport requires the IPC::Open2 module which is part of the
           standard perl distribution.  If this module is not loadable,
           attempting to use this transport will result in an error and
           program termination.

           --pipe [/path/to/command and arguments]
               Provide a process name and arguments to the process.  swaks
               will attempt to spawn the process and communicate with it via
               pipes.  If the argument is not an executable swaks will display
               an error and exit.

PROTOCOL OPTIONS
       These options are related to the protocol layer.

       -t, --to [email-address[,email-address,...]]
           Tells swaks to use argument(s) as the envelope-recipient for the
           email, or prompt for recipient if no argument provided.  If
           multiple recipients are provided and the recipient domain is needed
           to determine routing the domain of the last recipient provided is
           used.

           There is no default value for this option.  If no recipients are
           provided via any means, user will be prompted to provide one
           interactively.  The only exception to this is if a --quit-after
           value is provided which will cause the smtp transaction to be
           terminated before the recipient is needed.

       -f, --from [email-address]
           Use argument as envelope-sender for email, or prompt user if no
           argument specified.  The string <> can be supplied to mean the null
           sender.  If user does not specify a sender address a default value
           is used.  The domain-part of the default sender is a best guess at
           the fully-qualified domain name of the local host.  The method of
           determining the local-part varies.  On Windows, Win32::LoginName()
           is used.  On unix-ish platforms, the $LOGNAME environment variable
           is used if it is set.  Otherwise getpwuid(3) is used.  See also
           --force-getpwuid.

       --ehlo, --lhlo, -h, --helo [helo-string]
           String to use as argument to HELO/EHLO/LHLO command, or prompt use
           if no argument is specified.  If this option is not used a best
           guess at the fully-qualified domain name of the local host is used.
           If the Sys::Hostname module, which is part of the base
           distribution, is not available the user will be prompted for a HELO
           value.  Note that Sys::Hostname has been observed to not be able to
           find the local hostname in certain circumstances.  This has the
           same effect as if Sys::Hostname were unavailable.

       -q, --quit-after [stop-point]
           Point at which the transaction should be stopped.  When the
           requested stopping point is reached in the transaction, and
           provided that swaks has not errored out prior to reaching it,
           swaks will send "QUIT" and attempt to close the connection cleanly.
           These are the valid arguments and notes about their meaning.

           CONNECT, BANNER
               Terminate the session after receiving the greeting banner from
               the target.

           FIRST-HELO, FIRST-EHLO, FIRST-LHLO
               In a STARTTLS (but not tls-on-connect) session, terminate the
               transaction after the first of two HELOs.  In a non-STARTTLS
               transaction, behaves the same as HELO (see below).

           TLS Quit the transaction immediately following TLS negotiation.
               Note that this happens in different places depending on whether
               STARTTLS or tls-on-connect are used.  This always quits after
               the point where TLS would have been negotiated, regardless of
               whether it was attempted.

           HELO, EHLO, LHLO
               In a STARTTLS session, quit after the second HELO.  Otherwise
               quit after the first and only HELO.

           AUTH
               Quit after authentication.  This always quits after the point
               where authentication would have been negotiated, regardless of
               whether it was attempted.

           MAIL, FROM
               Quit after MAIL FROM: is sent.

           RCPT, TO
               Quit after RCPT TO: is sent.

       --timeout [time]
           Use argument as the SMTP transaction timeout, or prompt user if no
           argument given.  Argument can either be a pure digit, which will be
           interpretted as seconds, or can have a specifier s or m (5s = 5
           seconds, 3m = 180 seconds).  As a special case, 0 means don't
           timeout the transactions.  Default value is 30s.

       --protocol [protocol]
           Specify which protocol to use in the transaction.  Valid options
           are shown in the table below.  Currently the 'core' protocols are
           SMTP, ESMTP, and LMTP.  By using variations of these protocol types
           one can tersely specify default ports, whether authentication
           should be attempted, and the type of TLS connection that should be
           attempted.  The default protocol is ESMTP.  This table demonstrates
           the available arguments to --protocol and the options each sets as
           a side effect:

           SMTP
               HELO, "-p 25"

           SSMTP
               EHLO->HELO, "-tlsc -p 465"

           SSMTPA
               EHLO->HELO, "-a -tlsc -p 465"

           SMTPS
               HELO, "-tlsc -p 465"

           ESMTP
               EHLO->HELO, "-p 25"

           ESMTPA
               EHLO->HELO, "-a -p 25"

           ESMTPS
               EHLO->HELO, "-tls -p 25"

           ESMTPSA
               EHLO->HELO, "-a -tls -p 25"

           LMTP
               LHLO, "-p 24"

           LMTPA
               LHLO, "-a -p 24"

           LMTPS
               LHLO, "-tls -p 24"

           LMTPSA
               LHLO, "-a -tls -p 24"

       --pipeline
           If the remote server supports it, attempt SMTP PIPELINING (RFC
           2920).  This is a younger option, if you experience problems with
           it please notify the author.  Potential problem areas include
           servers accepting DATA even though there were no valid recipients
           (swaks should send empty body in that case, not QUIT) and deadlocks
           caused by sending packets outside the tcp window size.

       --force-getpwuid
           Tell swaks to use the getpwuid method of finding the default sender
           local-part instead of trying $LOGNAME first.

TLS / ENCRYPTION
       These are options related to encrypting the transaction.  These have
       been tested and confirmed to work with all three transport methods.
       The Net::SSLeay module is used to perform encryption when it is
       requested.  If this module is not loadable swaks will either ignore the
       TLS request or error out, depending on whether the request was
       optional.  STARTTLS is defined as an extension in the ESMTP protocol
       and will be unavailable if --protocol is set to a variation of smtp.
       Because it is not defined in the protocol itself, --tls-on-connect is
       available for any protocol type if the target supports it.

       -tls
           Require connection to use STARTTLS.  Exit if TLS not available for
           any reason (not advertised, negotiations failed, etc).

       -tlso, --tls-optional
           Attempt to use STARTTLS if available, continue with normal
           transaction if TLS was unable to be negotiated for any reason

       -tlsos, --tls-optional-strict
           Attempt to use STARTTLS if available.  Proceed with transaction if
           TLS is negotiated successfully or STARTTLS not advertised.  If
           STARTTLS is advertised but TLS negotiations fail, treat as an error
           and abort transaction.

       --tlsc, --tls-on-connect
           Initiate a TLS connection immediately on connection.  Following
           common convention, if this option is specified the default port
           changes from 25 to 465, though this can still be overridden with
           the --port option.

       --tls-get-peer-cert [/path/to/file]
           Get a copy of the TLS peer's certificate.  If no argument is given,
           it will be displayed to STDOUT.  If an argument is given it is
           assumed to be a filesystem path specifying where the certificate
           should be written.  The saved certificate can then be examined
           using standard tools such as the openssl command.  If a file is
           specified its contents will be overwritten.

AUTHENTICATION
       swaks will attempt to authenticate to the target mail server if
       instructed to do so.  This section details available authentication
       types, requirements, options and their interactions, and other fine
       points in authentication usage.  Because authentication is defined as
       an extension in the ESMTP protocol it will be unavailable if --protocol
       is set to a variation of smtp.

       All authentication methods require base64 encoding.  If the
       MIME::Base64 perl module is loadable swaks attempts to use it to
       perform these encodings.  If MIME::Base64 is not available swaks will
       use its own onboard base64 routines.  These are slower than the
       MIME::Base64 routines and less reviewed, though they have been tested
       thoroughly.  Using the MIME::Base64 module is encouraged.

       If authentication is required (see options below for when it is and
       isn't required) and the requirements aren't met for the authentication
       type available, swaks displays an error and exits.  Two ways this can
       happen include forcing swaks to use a specific authentication type that
       swaks can't use due to missing requirements, or allowing swaks to use
       any authentication type, but the server only advertises types swaks
       can't support.  In the former case swaks errors out at option
       processing time since it knows up front it won't be able to
       authenticate.  In the latter case swaks will error out at the
       authentication stage of the smtp transaction since swaks will not be
       aware that it will not be able to authenticate until that point.

       Following are the supported authentication types including any
       individual notes and requirements.

       The following options affect swaks' use of authentication.  These
       options are all inter-related.  For instance, specifying --auth-user
       implies --auth and --auth-password.  Specifying --auth-optional implies
       --auth-user and --auth-password, etc.

       -a, --auth [auth-type[,auth-type,...]]
           Require swaks to authenticate.  If no argument is given, any
           supported auth-types advertised by the server are tried until one
           succeeds or all fail.  If one or more auth-types are specified as
           an argument, each that the server also supports is tried in order
           until one succeeds or all fail.  This option requires swaks to
           authenticate, so if no common auth-types are found or no
           credentials succeed, swaks displays an error and exits.

           The following tables lists the valid auth-types

           LOGIN, PLAIN
               These basic authentication types are fully supported and tested
               and have no additional requirements

           CRAM-MD5
               The CRAM-MD5 authenticator requires the Digest::MD5 module.  It
               is fully tested and believed to work against any server that
               implements it.

           DIGEST-MD5
               The DIGEST-MD5 authenticator (RFC2831) requires the
               Authen::SASL module.  Version 20100211.0 and earlier used
               Authen::DigestMD5 which had some protocol level errors which
               prevented it from working with some servers.  Authen::SASL's
               DIGEST-MD5 handling is much more robust.

               The DIGEST-MD5 implementation in swaks is fairly immature.  It
               currently supports only the "auth" qop type, for instance.  If
               you have DIGEST-MD5 experience and would like to help swaks
               support DIGEST-MD5 better, please get in touch with me.

               The DIGEST-MD5 protocol's "realm" value can be set using the
               --auth-extra "realm" keyword.  If no realm is given, a
               reasonable default will be used.

               The DIGEST-MD5 protocol's "digest-uri" values can be set using
               the --auth-extra option.  For instance, you could create the
               digest-uri-value of "lmtp/mail.example.com/example.com" with
               the option "--auth-extra
               dmd5-serv-type=lmtp,dmd5-host=mail.example.com,dmd5-serv-name=example.com".
               The "digest-uri-value" string and its components is defined in
               RFC2831.  If none of these values are given, reasonable
               defaults will be used.

           CRAM-SHA1
               The CRAM-SHA1 authenticator requires the Digest::SHA module.
               This type has only been tested against a non-standard
               implementation on an Exim server and may therefore have some
               implementation deficiencies.

           NTLM/SPA/MSN
               These authenticators require the Authen::NTLM module.  Note
               that there are two modules using the Authen::NTLM namespace on
               CPAN.  The Mark Bush implementation (Authen/NTLM-1.03.tar.gz)
               is the version required by swaks.  This type has been tested
               against Exim, Communigate, and Exchange 2007.

               In addition to the standard username and password, this
               authentication type can also recognize a "domain".  The domain
               can be set using the --auth-extra "domain" keyword.  Note that
               this has never been tested with a mail server that doesn't
               ignore DOMAIN so this may be implemented incorrectly.

       -ao, --auth-optional [auth-type[,auth-type,...]]
           This option behaves identically to --auth except that it requests
           authentication rather than requiring it.  If no common auth-types
           are found or no credentials succeed, swaks proceeds as if
           authentication had not been requested.

       -aos, --auth-optional-strict [auth-type[,auth-type,...]]
           This option is a compromise between --auth and --auth-optional.  If
           no common auth-types are found, swaks behaves as if --auth-optional
           were specified and proceeds with the transaction.  If swaks can't
           support requested auth-type, the server doesn't advertise any
           common auth-types, or if no credentials succeed, swaks behaves as
           if --auth were used and exits with an error.

       -au, --auth-user [username]
           Provide the username to be used for authentication, or prompt the
           user for it if no argument is provided.  The string <> can be
           supplied to mean an empty username.

       -ap, --auth-password [password]
           Provide the password to be used for authentication, or prompt the
           user for it if no argument is provided.  The string <> can be
           supplied to mean an empty password.

       -ae, --auth-extra [KEYWORD=value[,...]]
           Some of the authentication types allow extra information to be
           included in the authentication process.  Rather than add a new
           option for every nook and cranny of each authenticator, the
           --auth-extra option allows this information to be supplied.

           The following table lists the currently recognized keywords and the
           authenticators that use them

           realm, domain
               The realm and domain keywords are synonymous.  Using either
               will set the "domain" option in NTLM/MSN/SPA and the "realm"
               option in DIGEST-MD5

           dmd5-serv-type
               The dmd5-serv-type keyword is used by the DIGEST-MD5
               authenticator and is used, in part, to build the digest-uri-
               value string (see RFC2831)

           dmd5-host
               The dmd5-host keyword is used by the DIGEST-MD5 authenticator
               and is used, in part, to build the digest-uri-value string (see
               RFC2831)

           dmd5-serv-name
               The dmd5-serv-name keyword is used by the DIGEST-MD5
               authenticator and is used, in part, to build the digest-uri-
               value string (see RFC2831)

       -am, --auth-map [auth-alias=auth-type[,...]]
           Provides a way to map alternate names onto base authentication
           types.  Useful for any sites that use alternate names for common
           types.  This functionality is actually used internally to map types
           SPA and MSN onto the base type NTLM.  The command line argument to
           simulate this would be "--auth-map SPA=NTLM,MSN=NTLM".  All of the
           auth-types listed above are valid targets for mapping except SPA
           and MSN.

       -apt, --auth-plaintext
           Instead of showing AUTH strings base64 encoded as they are
           transmitted, translate them to plaintext before printing on screen.

       -ahp, --auth-hide-password [replacement string]
           If this option is specified, any time a readable password would be
           printed to the terminal (specifically AUTH PLAIN and AUTH LOGIN)
           the password is replaced with a dummy string (or the contents of
           "replacement string" if provided).  The dummy string will be base64
           encoded or not contingent on the --auth-plaintext option.

           Note that --auth-hide-password is similar, but not identical, to
           the --protect-prompt option.  The former protects passwords from
           being displayed in the SMTP transaction regardless of how they are
           entered.  The latter protects sensitive strings when the user types
           them at the terminal, regardless of how the string would be used.

DATA OPTIONS
       These options pertain to the contents for the DATA portion of the SMTP
       transaction.

       -d, --data [data-portion]
           Use argument as the entire contents of DATA, or prompt user if no
           argument specified.  If the argument '-' is provided the data will
           be read from STDIN.  If any other argument is provided and it
           represents the name of an open-able file, the contents of the file
           will be used.  Any other argument will be itself for the DATA
           contents.

           The value can be on one single line, with \n (ascii 0x5c, 0x6e)
           representing where line breaks should be placed.  Leading dots will
           be quoted.  Closing dot is not required but is allowed.  The
           default value for this option is "Date: %DATE%\nTo:
           %TO_ADDRESS%\nFrom: %FROM_ADDRESS%\nSubject: test %DATE%\nX-Mailer:
           swaks v$p_version
           jetmore.org/john/code/swaks/\n%NEW_HEADERS%\n%BODY%\n".

           Very basic token parsing is performed on the DATA portion.  See
           --use-old-data-tokens for details about the single-character tokens
           marked as deprecated.  The following table shows the recognized
           tokens and their replacement values:

           %FROM_ADDRESS%
               Replaced with the envelope-sender.  Replaces the deprecated %F
               token.

           %TO_ADDRESS%
               Replaced with the envelope-recipient(s).  Replaces the
               deprecated %T token.

           %DATE%
               Replaced with the current time in a format suitable for
               inclusion in the Date: header.  Note this attempts to use the
               standard module Time::Local for timezone calculations.  If this
               module is unavailable the date string will be in GMT.  Replaces
               the deprecated %D token.

           %NEW_HEADERS%
               Replaced with the contents of the --add-header option.  If
               --add-header is not specified this token is simply removed.
               Replaces the deprecated %H token.

           %BODY%
               Replaced with the value specified by the --body option.  See
               --body for default.  Replaces the deprecated %H token.

       --use-old-data-tokens
           In previous versions of swaks the DATA tokens as described in the
           --data option above used single-character tokens (e.g., %F).  These
           were not a great choice for default tokens, and proved especially
           troublesome with encoded, non-english languages where these
           character combinations might be common.  The single-character
           tokens were replaced with the slightly-less-error-prone versions
           listed above.  The retention of the old tokens and the inclusion of
           this option to activate them are intended as a temporary aid to
           users who have an existing message corpus using the old tokens.
           The single-character tokens and the --use-old-data-tokens option
           should be considered deprecated and likely to be removed in the
           next release.

       -dab, --dump-as-body
           If --dump-as-body is used and no other option is used to changed
           the default body of the message, the body is replaced with output
           similar to the output of what is provided by --dump.  --dump's
           initial program capability stanza is not displayed, and the "data"
           section is not included.  Additionally, --dump always includes
           passwords.  By default --dump-as-body does not include passwords,
           though this can be changed with --dump-as-body-shows-password.

       -dabsp, --dump-as-body-shows-password
           Cause --dump-as-body to include plaintext passwords.  This option
           is not recommended.  This option implies --dump-as-body.

       --body [body-specification]
           Specify the body of the email.  The default is "This is a test
           mailing".  If no argument to --body is given, prompt to supply one
           interactively.  If '-' is supplied, the body will be read from
           standard input.  If any other text is provided and the text
           represents an open-able file, the content of that file is used as
           the body.  If it does not represent an open-able file, the text
           itself is used as the body.

           If the message is forced to MIME format (see --attach) the argument
           to this option will be included unencoded as the first MIME part.
           Its content-type will always be text/plain.

       --attach [attachment-specification]
           When one or more --attach option is supplied, the message is
           changed into a multipart/mixed MIME message.  The arguments to
           --attach are processed the same as --body with regard to stdin,
           file contents, etc.  --attach can be supplied multiple times to
           create multiple attachments.  By default each attachment is
           attached as a application/octet-stream file.  See --attach-type for
           changing this behavior.

           If a filename is specified, the MIME encoding will include that
           file name.  See --attach-name for more detail on file naming.

           It is legal for '-' (STDIN) to be specified as an argument multiple
           times (once for --body and multiple times for --attach).  In this
           case, the same content will be attached each time it is specified.
           This is useful for attaching the same content with multiple MIME
           types.

       --attach-type [mime-type]
           By default, content that gets MIME attached to a message with the
           --attach option is encoded as application/octet-stream.
           --attach-type changes the mime type for every --attach option which
           follows it.  It can be specified multiple times.

       --attach-name [name]
           This option sets the filename that will be included in the MIME
           part created for the next --attach option.  If no argument is set
           for this option, it causes no filename information to be included
           for the next MIME part, even if swaks could generate it from the
           local file name.

       -ah, --add-header [header]
           This option allows headers to be added to the DATA.  If %H is
           present in the DATA it is replaced with the argument to this
           option.  If %H is not present, the argument is inserted between the
           first two consecutive newlines in the DATA (that is, it is inserted
           at the end of the existing headers).

           The option can either be specified multiple times or a single time
           with multiple headers separated by a literal '\n' string.  So,
           "--add-header 'Foo: bar' --add-header 'Baz: foo'" and "--add-header
           'Foo: bar\nBaz: foo'" end up adding the same two headers.

       --header [header-and-data], --h-Header [data]
           These options allow a way to change headers that already exist in
           the DATA.  '--header "Subject: foo"' and '--h-Subject foo' are
           equivalent.  If the header does not already exist in the data then
           this argument behaves identically to --add-header.  However, if the
           header already exists it is replaced with the one specified.

       -g  If specified, swaks will read the DATA value for the mail from
           STDIN.  This is equivalent to "--data -".  If there is a From_ line
           in the email, it will be removed (but see -nsf option).  Useful for
           delivering real message (stored in files) instead of using example
           messages.

       --no-data-fixup, -ndf
           This option forces swaks to do no massaging of the DATA portion of
           the email.  This includes token replacement, From_ stripping,
           trailing-dot addition, --body/attachment inclusion, and any header
           additions.  This option is really only useful when used with
           --data, since the internal default DATA portion uses tokens.

       --no-strip-from, -nsf
           Don't strip the From_ line from the DATA portion, if present.

OUTPUT OPTIONS
       By default swaks provides a transcript of its transactions to its
       caller (STDOUT/STDERR).  This transcript aims to be as faithful a
       representation as possible of the transaction though it does modify
       this output by adding informational prefixes to lines and by providing
       plaintext versions of TLS transactions

       The "informational prefixes" are referred to as transaction hints.
       These hints are initially composed of those marking lines that are
       output of swaks itself, either informational or error messages, and
       those that indicate a line of data actually sent or received in a
       transaction.  This table indicates the hints and their meanings:

       === Indicates an informational line generated by swaks

       *** Indicates an error generated within swaks

       ->  Indicates an expected line sent by swaks to target server

       ~>  Indicates a TLS-encrypted, expected line sent by swaks to target
           server

       **> Indicates an unexpected line sent by swaks to the target server

       *~> Indicates a TLS-encrypted, unexpected line sent by swaks to target
           server

       >   Indicates a raw chunk of test sent by swaks to a target server (see
           --show-raw-text).  There is no concept of "expected" or
           "unexpected" at this level.

       <-  Indicates an expected line sent by target server to swaks

       <~  Indicates a TLS-encrypted, expected line sent by target server to
           swaks

       <** Indicates an unexpected line sent by target server to swaks

       <~* Indicates a TLS-encrypted, unexpected line sent by target server to
           swaks

       <   Indicates a raw chunk of text received by swaks from a target
           server (see --show-raw-text).  There is no concept of "expected" or
           "unexpected" at this level.

       The following options control what and how output is displayed to the
       caller.

       -n, --suppress-data
           Summarizes the DATA portion of the SMTP transaction instead of
           printing every line.  This option is very helpful, bordering on
           required, when using swaks to send certain test emails.  Emails
           with attachments, for instance, will quickly overwhelm a terminal
           if the DATA is not supressed.

       -stl, --show-time-lapse [i]
           Display time lapse between send/receive pairs.  This option is most
           useful when Time::HiRes is available, in which case the time lapse
           will be displayed in thousandths of a second.  If Time::HiRes is
           unavailable or "i" is given as an argument the lapse will be
           displayed in integer seconds only.

       -nth, --no-hints
           Don't show transaction hints (useful in conjunction with -hr to
           create copy/paste-able transactions).

       -raw, --show-raw-text
           This option will print a hex dump of raw data sent and received by
           swaks.  Each hex dump is the contents of a single read or write on
           the network.  This should be identical to what is already being
           displayed (with the exception of the \r characters being removed).
           This option is useful in seeing details when servers are sending
           lots of data in single packets, or breaking up individual lines
           into multiple packets.  If you really need to go in depth in that
           area you're probably better with a packet sniffer, but this option
           is a good first step to seeing odd connection issues.

       --output-file </path/to/file>
       --output-file-stdout </path/to/file>
       --output-file-stderr </path/to/file>
           These options allow the user to send output to files instead of
           stdout/stderr.  The first option sends both to the same file.  The
           arguments of &STDOUT and &STDERR are treated specially, refering to
           the "normal" file handles, so "--output-file-stderr '&STDOUT'"
           would redirect STDERR to STDOUT.

       -pp, --protect-prompt
           Don't echo user input on prompts that are potentially sensitive
           (right now only authentication password).  See also
           --auth-hide-password

       -hr, --hide-receive
           Don't display lines sent from the remote server being received by
           swaks

       -hs, --hide-send
           Don't display lines being sent by swaks to the remote server

       -hi, --hide-informational
           Don't display non-error informational lines from swaks itself.

       -ha, --hide-all
           Do not display any content to the terminal.

       -S, --silent [level]
           Cause swaks to be silent.  If no argument is given or if an
           argument of "1" is given, print no output unless/until an error
           occurs, after which all output is shown.  If an argument of "2" is
           given, only print errors.  If "3" is given, show no output ever.

       --support
           Print capabilities and exit.  Certain features require non-standard
           perl modules.  This options evaluates whether these modules are
           present and displays which functionality is available and which
           isn't, and which modules would need to be added to gain the missing
           functionality.

       --dump
           This option causes swaks to print the results of option processing,
           immediately before mail would have been sent.  No mail will be sent
           when --dump is used.  Note that --dump is considered to be a pure
           self-diagnosis tool and no effort is made or will ever be made to
           mask passwords in the --dump output.

       --help
           Display this help information.

       --version
           Display version information.

PORTABILITY
       OPERATING SYSTEMS
           This program was primarily intended for use on unix-like operating
           systems, and it should work on any reasonable version thereof.  It
           has been developed and tested on Solaris, Linux, and Mac OS X and
           is feature complete on all of these.

           This program is known to demonstrate basic functionality on Windows
           using ActiveState's Perl.  It has not been fully tested.  Known to
           work are basic SMTP functionality and the LOGIN, PLAIN, and
           CRAM-MD5 auth types.  Unknown is any TLS functionality and the
           NTLM/SPA and DIGEST-MD5 auth types.

           Because this program should work anywhere Perl works, I would
           appreciate knowing about any new operating systems you've
           thoroughly used swaks on as well as any problems encountered on a
           new OS.

       MAIL SERVERS
           This program was almost exclusively developed against Exim mail
           servers.  It was been used casually by the author, though not
           thoroughly tested, with Sendmail, Smail, Exchange, Oracle
           Collaboration Suite, qpsmtpd, and Communigate.  Because all
           functionality in swaks is based off of known standards it should
           work with any fairly modern mail server.  If a problem is found,
           please alert the author at the address below.

EXIT CODES
       0   no errors occurred

       1   error parsing command line options

       2   error connecting to remote server

       3   unknown connection type

       4   while running with connection type of "pipe", fatal problem writing
           to or reading from the child process

       5   while running with connection type of "pipe", child process died
           unexpectedly.  This can mean that the program specified with --pipe
           doesn't exist.

       6   Connection closed unexpectedly.  If the close is detected in
           response to the 'QUIT' swaks sends following an unexpected
           response, the error code for that unexpected response is used
           instead.  For instance, if a mail server returns a 550 response to
           a MAIL FROM: and then immediately closes the connection, swaks
           detects that the connection is closed, but uses the more specific
           exit code 23 to detail the nature of the failure.  If instead the
           server return a 250 code and then immediately closes the
           connection, swaks will use the exit code 6 because there is not a
           more specific exit code.

       10  error in prerequisites (needed module not available)

       21  error reading initial banner from server

       22  error in HELO transaction

       23  error in MAIL transaction

       24  no RCPTs accepted

       25  server returned error to DATA request

       26  server did not accept mail following data

       27  server returned error after normal-session quit request

       28  error in AUTH transaction

       29  error in TLS transaction

       32  error in EHLO following TLS negotiation

ABOUT THE NAME
       The name "swaks" is a (sort-of) acronym for "SWiss Army Smtp".  It was
       chosen to be fairly distinct and pronounceable.  While "swaks" is
       unique as the name of a software package, it has some other, non-
       software meanings.  Please send in other uses of "swak" or "swaks" for
       inclusion.

       "Sealed With A Kiss"
           SWAK/SWAKs turns up occasionally on the internet with the meaning
           "with love".

       bad / poor / ill (Afrikaans)
           Seen it in the headline "SA se bes en swaks gekledes in 2011",
           which was translated as "best and worst dressed" by native
           speakers.  Google Translate doesn't like "swaks gekledes", but it
           will translate "swak" as "poor" and "swak geklede" as "ill-
           dressed".

CONTACT
       proj-swaks@jetmore.net
           Please use this address for general contact, questions, patches,
           requests, etc.

       updates-swaks@jetmore.net
           If you would like to be put on a list to receive notifications when
           a new version of swaks is released, please send an email to this
           address.

       http://www.jetmore.org/john/code/swaks/
           Change logs, this help, and the latest version is found at this
           link.



perl v5.14.2                      2012-03-21                          SWAKS(1)
```

Example Usage
-------

Links
-------

