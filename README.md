# dreamland_fenia_public

[![Stand With Ukraine](https://raw.githubusercontent.com/vshymanskyy/StandWithUkraine/main/badges/StandWithUkraine.svg)](https://stand-with-ukraine.pp.ua)

Public Fenia scripts for [DreamLand MUD](https://github.com/dreamland-mud/dreamland_code). Fenia is the scripting language the game uses for spells, skills, mob and object behavior, and quests. This repository is a library you can read, copy and extend.

## What is inside

| Folder | Holds |
|---|---|
| `utils/` | Helper functions such as chance rolls, currency, inflection, translit, time, weight and room, mob and object helpers |
| `spell/` | An example spell (`armor`) |
| `skillcommand/` | An example skill command (`camp`) |
| `areas/` | Scripts for two zones, `midgaard.are` and `under2.are` |

Each script is a plain file without an extension. Folder names follow the layout the game expects, for example `spell/<name>/runVict`.

## Where it mounts

In a local server this repository is cloned into `share/DL/fenia/public`:

```bash
cd /path/to/runtime
git clone https://github.com/dreamland-mud/dreamland_fenia_public.git share/DL/fenia/public
```

See the [dreamland_code README](https://github.com/dreamland-mud/dreamland_code#readme) for the full server setup.

## Load a script locally

Scripts are not read at boot. You load them from inside the game as a character with coder rights (the default `Kadm` and `Cadmus` characters have them). `feniaScriptDir` in `etc/dreamland.xml` must be `share/DL/fenia`, because the stock value `share/DL/fenia.local` does not contain the `public` folder. Stop the server before you edit that file. It writes its in-memory copy back every game tick and on shutdown, and it reads `feniaScriptDir` only at start.

```text
cs load public/utils/translit
```

A name that starts with `public/` is looked up in this repository. Paths may contain spaces (`public/utils/object: dimensions`). Type them as they are, without quotes. Some helpers call private namespaces that are not in this repository, so not every helper runs on a local server. `utils/translit` and `utils/inflect` need only `.tmp.system`, which the seeded database already has.

## More

* [Fenia](https://github.com/dreamland-mud/dreamland_code/wiki/Fenia): the language and how the game uses it
* [Fenia-API](https://github.com/dreamland-mud/dreamland_code/wiki/Fenia-API): objects, methods and the helpers from this repository
* [Fenia-Scripts](https://github.com/dreamland-mud/dreamland_code/wiki/Fenia-Scripts): file layout, `cs load` and the web editor
* [Repositories](https://github.com/dreamland-mud/dreamland_code/wiki/Repositories): how the repositories fit together

## License

GPLv3. See `LICENSE`.
