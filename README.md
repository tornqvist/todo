# todo
My personal todo manager. Partly an exercise in bash and partly an excuse to procrastinate.

Made for macOS and syncing over iCloud. It puts a `todo` file in your `~/Documents` folder which server as a log and database.

Todos can be tagged with a `+` and attached to a context with an `@`

## Usage

Add [todo](todo) to your path (i.e. put a copy into `~/bin`) and call it from your `.bash_profile`. This will print all todos whenever you open a new terminal window.

```bash
$ echo todo >> ~/.bash_profile
```

To filter todos you can add something more advanced that lets you apply an automatic filter:

```bash
# in your ~/.bash_profile
PROGRAM="`which todo`"
function todo() {
  $PROGRAM "$@" | grep "$TODO_FILTER"
}
todo
```

```bash
$ export TODO_FILTER=+my-project
$ todo # <- show only todos tagged with "my-project"
```

### Commands
Just calling `todo` will print all undone todos. Todos can be added by appending a string to the command.

```bash
$ todo water the flowers @home
```

A series of commands can be used to add, unset (remove) and mark todos as done.

- `--add, -a` add a new todo
- `--unset, -u` unset a todo
- `--done, -x` mark todo as done
- `--log, -l` list all done todos
- `--help, -h` show help text
- `--verbose, -v` show meta information

```bash
$ todo --add "water the flowers @home" # add new todo
$ todo --unset 2 # remove todo #2, not marking it as done
$ todo -x 1 # mark todo #1 as done
```
