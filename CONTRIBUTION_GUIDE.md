## Kelp Strategy Compendium Contribution Guide

So you'd like to share your Kelp strategy here in the compendium. Great! Here's what you need to know.

### Requirements for Inclusion

Before you contribute, please ask yourself: would I trust my tokens to this code? Or better yet: *have I already trusted my tokens to this code*?
We don't ask that you prove you made money or anything like that, just make sure you're confident that the strategy is worth using!

1. Your strategy must be written in Go and compilable as an integrated component of a Kelp build
2. Your strategy must be deployable; it must successfully place orders on the Stellar network
3. Your strategy must not modify the core Kelp code in such a way that your build could not run the out-of-the-box strategies.
This is to ensure that others who use your strategy can integrate it with the rest of their Kelp build.
4. You must provide detailed documentation of your strategy. This should include:

   - The rationale that led you to make the strategy
   - How your strategy accomplishes what you wanted it to do
   - What the configuration variables are and how they work
   - Instructions for integrating your strategy's code with a Kelp build
   - Any special considerations for effectively deploying your strategy
   
### Specific File Requirements

At minimum your strategy will need:

1. The strategy code files themselves for inclusion in the Kelp _plugins_ package
   - *[strategyName]LevelProvider.go*
   - *[strategyName]Strategy.go*
2. A configuration file in TOML format, named *[strategyName].cfg*
3. The code to add to *factory.go* to make your strategy callable from the command line, named *addTo_factory.go*
4. Your documentation file, named *README.md*

If your strategy needs additional components added to the core Kelp code, include them as *addTo_[path/filename]*. 
For example you might have *addTo_support/utils/functions.go*. Remember to **add**, not **overwrite**. 
You do not need to include the rest of the core file, just tell us where it goes.

Please base your strategy's code on either the most recent Kelp release or a current copy of the Kelp *master* branch.
Include in your documentation the *./kelp version* output for the build you tested your strategy with.
It will look something like this:

````
version: v1.0.0-rc1
git hash: 337f478b0e7a1dc235aef31788754bc1ab11b6a1
build date: 20180813T231816Z
GOOS: linux
GOARCH: amd64
````

### Code Style

It's a good idea to follow the Kelp code conventions as much as feasible. 
For example, you may have noticed that Kelp doesn't use `else` statements, and uses `e` for the error return variable. 
This just makes it easier for all of us to read your code and integrate it with our own Kelp builds. We'll try not to nitpick!

### Contribution Process

When your strategy is ready to go:

1. Fork this repository 
2. Create a topic branch on your fork for your strategy
2. Add a folder named for your strategy to that branch, containing all your strategy's files
3. Submit a pull request

Someone will review your contribution, and ask questions or suggest revisions as appropriate.

If you would like to maintain your strategy's code here in the compendium we can set you up as a Kelp Forest member and make you the code owner for your folder.
If not, we'll maintain your folder and manage additional contributions to it, giving any pull requests from you priority over third parties.

### Intellectual Property Information

Kelp is an open-source project and we want to maintain an open-source ethos too.

Anything you contribute to the compendium remains your intellectual property. However, the compendium uses the open-source MIT license, so please do not contribute anything you wish to keep proprietary. 
Contribution to the compendium does not grant other contributors any rights to your work beyond those of the MIT license. 
If you're not familiar with the MIT license it's a good idea to [read through it](https://github.com/kelpbot-forest/kelp-strategies/blob/master/LICENSE). 
