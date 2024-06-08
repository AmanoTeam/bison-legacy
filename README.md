GCC versions older than 4.1 fail to build with modern versions of Bison, producing the following error:

```c
c-parse.y: In function 'yyparse':
c-parse.y:594:16: error: 'YYLEX' undeclared (first use in this function)
       yychar = YYLEX;
```

For GCC 3.3 and older, the build instead fails with:

```c
c-parse.y:1664.19-20: error: $$ for the midrule at $4 of ‘structsp_attr’ has no declared type
c-parse.y:1674.19-20: error: $$ for the midrule at $4 of ‘structsp_attr’ has no declared type
c-parse.y:1682.19-20: error: $$ for the midrule at $4 of ‘structsp_attr’ has no declared type
c-parse.y:1687.19-20: error: $$ for the midrule at $3 of ‘structsp_attr’ has no declared type
```

For building GCC 3.4–4.0, Bison 2.7 is sufficient. For GCC <= 3.3, you will need Bison 2.3.

To fix this, download the corresponding [Bison binaries](https://github.com/AmanoTeam/bison-legacy/releases), unpack them somewhere, and add them to your `PATH`:

```bash
export PATH=/tmp/bison/bin:$PATH
export BISON_PKGDATADIR=/tmp/bison/share/bison
```
