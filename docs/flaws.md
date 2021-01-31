## Flaws

In this document, I just describe some of the shortcomings I see in LuaRocks: things I'd like to improve, really.

### Clear and useful errors

It's not uncommon to get an error such as `file source and destination cannot be the same` to tell you that the file does not actually exist. At one point, you get used to this, but I think the error messages are not user-friendly at all. They are not descriptive enough and often leave you going in circles or wondering what to do, resorting to searching the error online.

### Better rockspecs

Rockspecs aren't *bad*, but they could be better. Here's why.

#### Format

Personally, they are painful to write, but this might not be the case for everyone. This has caused me to write projects like [rockwriter][1] or [rockbuild][2]. I would love to see a cleaner format, that is just easier to write. This could still be compiled into static, versioned rockspecs that are serialized Lua tables. But, the user-facing rockspecs should be easier to write.

#### Versioning

`luarocks new_version` and versioned files are too rigid. LuaRocks complains if the name isn't exactly right, and `new_version` is just a bunch of configurable fields thrown into a command. I would much prefer some sort of `rock.lua` file whose version can be bumped.

### Better interfaces

Interfacing with LuaRocks can be hard on several fronts:

#### CLI tool

The LuaRocks CLI tool does not even let you install more than one package at once, forcing you to type the same command over and over. The list command has unnecessary newlines, everything is plain white... I feel like this could be massively improved to be much more user friendly, nicer to look at... Options to output as JSON/Lua tables could be enabled if we needed to build utility belts.

#### Webpage

Ever since the last revision, there are several things that I've changed my mind about here. The current page is fairly good, yet I can't help but side-eye [Hackage][3]. Its main page is not that attractive and could be improved, but the general *feel* of a [package description][4] is something I could go for.

More stats would also be nice, but not a requirement.

As for documentation, there will be more on that later.

### Dependencies

LuaRocks has a fair dependency handling, but it isn't powerful enough. While LuaRocks 3 got build dependencies and test dependencies, there is no such thing as optional dependencies, or "install one of"s. The latter can be useful for JSON parsing modules, for example.

### Language support

LuaRocks only works for Lua, and if you use another language that compiles to Lua, you're on your own. You have to compile and provide the files yourself, and it really doesn't make it easy or clean. [Teal][5] struggles to get type declaration files integrated on LuaRocks, and you have to keep all build artifacts for [MoonScript][6]. It doesn't all end here though; there are other languages like Amulet or Fennel that could use LuaRocks support.

### Documentation

Right now, documentation for rocks is kind of a free for all. Most people use [LDoc][7], there are things like [Fir][8], but they are all external and hosted on GitHub Pages or similar. It would be cool to have a centralized documentation repository like [Hackage][9] does with [Haddock][4]. Benefits of this would include being to reference any other rock, consistent styling, and even other features regarding source code analysis which I will go in depth when I release another of my projects. Feel free to contact me about this.

### File management

Right now, LuaRocks forces you to include files in your rockspecs based on Lua modules, and including other files that are not Lua modules or C libraries becomes hard. LuaRocks should just move all specified files over regardless of filetype, because the way it does it right now can be quite confusing. Some files even get renamed in the process.

[1]: https://github.com/daelvn/rockwriter	"daelvn/rockwriter"
[2]: https://github.com/daelvn/rockbuild	"daelvn/rockbuild"
[3]: https://hackage.haskell.org "Haskell Hackage"
[4]: https://hackage.haskell.org/package/haddock "Haddock"
[5]: https://github.com/teal-language/tl "Teal"
[6]: https://github.com/leafo/moonscript "MoonScript"
[7]: https://github.com/lunarmodules/LDoc "LDoc"
[8]: https://github.com/daelvn/fir "Fir"
[9]: https://hackage.haskell.org/package/base-4.14.1.0/docs/Control-Monad.html "Control.Monad (base) documentation on Haskell Hackage"