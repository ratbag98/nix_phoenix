# Elixir, Phoenix and Postgres flake

## Installation

```bash
mkdir -p new_project_dir
cd new_project_dir
git clone https://github.com/ratbag98/nix_phoenix.git .
```

Ignore the error message about `direnv allow` for now. Check the version
numbers in `flake.nix` are what you need, then:

```bash
rm -rf .git
direnv allow
pg_ctl -D ./postgres -l logfile start
```

You can now create an Elixir project inside the `new_project_dir`:

```bash
mix new new_app
```

or create a new Phoenix app:

```bash
mix phx.new new_phoenix_app
```

If you did both you'll end up with this structure:

```text
README.md
flake.lock
flake.nix
logfile
new_app/
new_phoenix_app/
postgres/
```

Suggest you then make `new_app` or `new_phoenix_app` into a git repository (ie
keep all this stuff out of the project repo).

## Postgres control

You'll need to stop the postgres manually. Make sure you're in a subdirectory
of the `new_project_dir` and then:

```bash
pg_ctl stop
```

Next time start the server as above:

```bash
cd new_project_dir
pg_ctl -D ./postgres -l logfile start
```
