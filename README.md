# Phel Cli Skeleton

Example code for https://github.com/phel-lang/phel-lang/issues/778

Running code with `vendor/bin/phel run src/main.phel` works fine, output is as expected without error.

However evaluating logic in `main.phel` manually in REPL fails:

```
$ vendor/bin/phel repl

phel:1> (require cli-skeleton\modules\defstruct-module)
calling defstruct in defstruct-module
cli-skeleton\modules\defstruct-module
phel:2> (require cli-skeleton\modules\defstruct-referring-module)
calling defstruct in defstruct-module

Fatal error: Cannot declare class cli_skeleton\modules\defstruct_module\my_struct, because the name is already in use in /tmp/__phelLw1j3N on line 5
```
