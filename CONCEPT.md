# Meteor concept

Let's try to make a LuaRocks replacement that is not garbage and can actually aspire to be better.

## Name

For now, I like Meteor. Other names could be Conifer, Fir, Eukaryos (lame biology joke),  arx/ars…

This is not very important for now.

## Better rockspecs

The inspiration behind my tool [rockwriter][rockwriter] wasn't that complex. Rockspecs are a pain in the ass to write, so I came up with a better way to write them. Constructing big Lua tables in general by hand is a pain in the ass. Let's not repeat this error and make concise package specs.

## Clear and useful errors

Every once in a while, LuaRocks will hit you with "file source and destination cannot be the same" to tell you that the file does not actually exist. That's garbage.  Others include yelling at you about the rockspec name, and god, renaming is a real pain in the ass. Let's get these useless errors out of the way, let's actually serve the user.

## Better interfaces

The LuaRocks CLI tool does not even let you install more than one package at once, forcing you to type the same command over and over. The list command has unnecessary newlines, everything is plain white…

The LuaRocks page is fairly good, but perhaps I'd like it to be more like the [AUR][AUR], with basic actually useful voting (LR lets you star, but it doesn't actually change anything), a bit more info on dependencies…

## Automatically-generated rockspecs

I think we're already grown up to be able to generate basic rockspecs for basic projects. LuaRocks does this but not very publicly availiable, let's make this easier.

## Windows

For some reason, people decide it's a good idea to do programming on Windows. Raw. No WSL. On pure Windows.

If they ever get excused from hell, let's actually make this run on Windows without wanting to shoot yourself, as everyone describes it.

## Path mess

LuaRocks has a bit of a path mess, we could aim to improve that. It's not that bad though.

## Proper dependencies

LuaRocks has a fair dependency handling,  but certainly no optional dependencies or anything like that. That might be neat.

I was also thinking of being able to declare "install one of". My program debugkit for example, lets you use `rxi-json-lua`, `lua-cjson-2` and `dkjson` as JSON encoder providers.

## Mostly pure Lua (eh well)

We can try to keep it pure Lua, and by using my library [filekit][filekit] we could even get cross-compat with ComputerCraft if we really tried and cared.

## Better project management

LuaRocks doesn't care at all about your folder structure, your documentation, your source control, etc. That can be a good and a bad thing. I'm going to put some proposals below.

### LICENSE and README automatic addition

As simple as initializing the package and just adding these two files, perhaps even with license presets.

### User-defined project structure

With defaults, let the user define a project structure, such as where to keep source code, where to keep docs, where to keep tests…

### Documentation

Provide embedded commands that use external tools to build documentation. Namely LDoc, Locco/Docco and MkDocs.

### Git awareness

Let's make the project manager aware that git exists, by enabling releases, pushing, .gitattributes, .gitignore, etc.

### Builds

Allow the project to be built with a custom building tool. Even if it's just MoonScript, C modules, a makefile, whatever. Make something that works for everyone.

### MoonScript friendly

LuaRocks requires you to precompile MoonScript before packaging for portability since it really can't build itself (not without hard tweaking), so let's just make it MS-friendly by precompiling, packaging and removing the files.

[rockwriter]: https://github.com/daelvn/rockwriter	"rockwriter"
[AUR]: https://aur.archlinux.org	"AUR"
[filekit]: https//git.daelvn.ga/filekit/	"filekit"

