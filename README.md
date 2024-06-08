GCC versions older than 4.1 fail to build with the following error when using a modern Bison version:

```c
c-parse.y: In function 'yyparse':
c-parse.y:594:16: error: 'YYLEX' undeclared (first use in this function)
       yychar = YYLEX;
```

To fix this, download the corresponding [Bison 2.7 binaries](https://github.com/AmanoTeam/bison-legacy/releases/tag/nightly), unpack them somewhere, and add them to your `PATH`:

```bash
export PATH=/tmp/bison/bin:$PATH
export BISON_PKGDATADIR=/tmp/bison/share/bison
```

For reference, this issue was fixed upstream in GCC 4.1 with commit: [27bf414](https://github.com/gcc-mirror/gcc/commit/27bf414caa1a1d61601b0255020df9c4ae765e9c). Theoretically, it’s possible to backport the fix to older releases, but it seems like too much trouble.