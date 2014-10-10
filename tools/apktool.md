# apktool

Notes
-------
A tool for reverse engineering Android apk files


Help Text
-------
```
Apktool v1.5.2 - a tool for reengineering Android apk files
Copyright 2010 Ryszard Wiśniewski <brut.alll@gmail.com>
with smali v1.4.1, and baksmali v1.4.1
Updated by @iBotPeaches <connor.tumbleson@gmail.com> 
Apache License 2.0 (http://www.apache.org/licenses/LICENSE-2.0)

Usage: apktool [-q|--quiet OR -v|--verbose] COMMAND [...]

COMMANDs are:

    d[ecode] [OPTS] <file.apk> [<dir>]
        Decode <file.apk> to <dir>.

        OPTS:

        -s, --no-src
            Do not decode sources.
        -r, --no-res
            Do not decode resources.
        -d, --debug
            Decode in debug mode. Check project page for more info.
        -b, --no-debug-info
            Baksmali -- don't write out debug info (.local, .param, .line, etc.)
        -f, --force
            Force delete destination directory.
        -t <tag>, --frame-tag <tag>
            Try to use framework files tagged by <tag>.
        --frame-path <dir>
            Use the specified directory for framework files
        --keep-broken-res
            Use if there was an error and some resources were dropped, e.g.:
            "Invalid config flags detected. Dropping resources", but you
            want to decode them anyway, even with errors. You will have to
            fix them manually before building.

    b[uild] [OPTS] [<app_path>] [<out_file>]
        Build an apk from already decoded application located in <app_path>.

        It will automatically detect, whether files was changed and perform
        needed steps only.

        If you omit <app_path> then current directory will be used.
        If you omit <out_file> then <app_path>/dist/<name_of_original.apk>
        will be used.

        OPTS:

        -f, --force-all
            Skip changes detection and build all files.
        -d, --debug
            Build in debug mode. Check project page for more info.
        -a, --aapt
            Loads aapt from specified location.

    if|install-framework <framework.apk> [<tag>] --frame-path [<location>] 
        Install framework file to your system.

For additional info, see: http://code.google.com/p/android-apktool/
For smali/baksmali info, see: http://code.google.com/p/smali/
```

Example Usage
-------


```
apktool d application.apk
```

Links
-------
[apktool Google project](https://code.google.com/p/android-apktool/)

[apktool Bitbucket project](https://bitbucket.org/iBotPeaches/apktool/downloads)
