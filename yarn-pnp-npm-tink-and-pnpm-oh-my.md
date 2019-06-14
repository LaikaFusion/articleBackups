
# Yarn PnP, npm tink, and pnpm Oh My

## Photo by chuttersnap on Unsplash

At this point everyone knows not to push their Node Modules folder to Github. The size of it alone confuses Git and it better to just run the install command. The Node Modules in every project on your machine is a fresh folder and likely has duplicates of dependencies you have for other projects. There have in the last few years been a few takes on how to fix this.

## History

First though a brief history lesson. When you think of Javascript package managers there is one you think of above all others. npm and their repository of 830,134 modules [(at time of writing)](http://www.modulecounts.com/) is the root of everything else in this article. While there have been rough spots over the years, [the left-pad incident](https://www.infoworld.com/article/3047177/how-one-yanked-javascript-package-wreaked-havoc.html), [breaking Linux system files](https://github.com/npm/npm/issues/19883), and [malicious code being added to packages](https://github.com/eslint/eslint-scope/issues/39), it has remained the top used tool for the job. npm also has npx which allows a module to download and run in one go. For things like `create-react-app` this ensures you always run an up to date copy.

A more recent entry is Yarn. This is a Facebook produced package manager that when it was new added some distinct advantages over npm. For one it generated a lock file, that guaranteed that the version of the package you used is the package everyone else uses until the lockfile is updated. It also did things like cached packages, and used proxy of the main npm modules to allow faster installs. Since it’s release though, npm has released a new version that both increased the speed and added a lockfile mechanisms. As of right now the general blog consensus seems to be they’re both [about the same](https://medium.com/@vincentnewkirk/npm-vs-yarn-2019-e88757b17038).

Both npm and Yarn still have the duplicate node modules problem I talked about earlier. While Yarn caches modules on your machine so redownloading happens even quicker it does not change the fact you multiple copies on your machine. There are a few fixes in the works from both companies.

## Solutions to the Problem

### Yarn PnP

Reading my previous article on `create-react-app`([What Does Create React App Actually Do?](https://medium.com/@Andrew_Mc/what-does-create-react-app-actually-do-73c899443d61)), you may have noticed references to something called Plug’n’Play (PnP). Not to be confused with Universal Plug and Play or pnpm (which will be covered bellow), this is a feature unveiled by Yarn in September of 2018. Rather then the file being there, it instead points to cache where the file actually is. It uses a file called `pnp.js`which acts as a map to where in the cache these are located.

What this means is both faster install times, and less disk space when you have a higher number of projects or a single project with a lot of shared dependencies. If two libraries both require a modules instead of two copies in your node module folder, there will be only one. For me it is easiest to test the speed. Running `npx create-react-app` without pnp enabled took 10.62 seconds. With it enabled that dropped to 4.09 seconds. That’s just over two and half times faster just by adding a flag to `create-react-app`.

PnP is a specification, not a feature exclusive to Yarn. Other package managers for JS modules can implement it if they wish. NPM has no plans to do so at this time because what I will talk about next. If I’ve sold you on using it, check out the short guide on that down bellow. If not keep reading for some alternatives.

### npm tink

Just after Yarn PnP was announced, npm announced tink. This had previously been called crux but was renamed due to an existing module already using that name. tink is going to replace npm at some point (and be renamed to npm) but as of right now it is experimental client. PnP and tink have a different philosophy. Where as PnP is something strapped onto the existing tools, tink rewrites them. It mostly does not have a node_modules folder at all. Instead your dependencies go to a cache. That does sound rather like PnP so far. The difference is that tink actually replaces more then npm, it also replaces Node. When Node goes to find a module, it splits in and says “No wait check here” and points to tink’s central cache. It lets you load things that are not js files too like Typescript or JSX, and with any import or require in those files.

There is obviously more complexity to this approach. While PnP can be used now, tink must be downloaded separately and run separately. Both these solutions coming out around the same time is interesting, but not too surprising. It makes sense this is the direction that package managers would go in, as they do handle the same files again and again.

In fact these projects are not the first to tackle the Node Modules duplication problem. That honor goes to pnpm, which stands for preformant npm. This came out in 2017 and attempts to tackle the duplication like the other two do. The way it works is via system set up hard links. Hard links a feature built into the OS which makes it appear that a file is in two places at once while only taking up one spot on the disk. Think of it like two different doors to the same room, rather then to two identical separate rooms.

### pnpm

pnpm is not as widely used as either Yarn or npm but it does list Microsoft as one of the groups creating projects with it. Is this approach better? From a compatibility stand point most likely. It really adds nothing new, no new requirements files, or modified Node versions. It just uses an OS feature that has existed for forty years to solve a common problem. There is however an issue with cross compatibility. Windows does not really work the same way Linux, or MacOS do. This is extra work for the pnpm dev. This combined with the fact it is made and supported by a smaller team which does not have the financial backing of a company like npm or Facebook may make it a worse choice in the long run.

### Everything Else

What else? Besides brief mentions of things like [Turbo](https://medium.com/stackblitz-blog/introducing-turbo-5x-faster-than-yarn-npm-and-runs-natively-in-browser-cc2c39715403) the only other interesting bit I found is [@pika/web](https://www.pikapkg.com/blog/pika-web-a-future-without-webpack/) this seems to be attempting to go after npm and webpack at the same time for web frontend. It is only a few months old so it has not really had time to pick up steam yet. It seems to be more of a replacement for Bower which is depreciated as of a few years ago. This may be something to keep an eye on depending on what you do.

## Yarn PnP Tutorial

As promised this will be a short PnP tutorial. The length is short because it really is that easy. If you want to add it to your existing project make sure you have at least Yarn version 1.12 or higher. If you are sure you do, then all that is needed is a `yarn -pnp` command run at the the level of your `package.json.` This will add to your package.json and rerun yarn install in one command.

If you want to use `create-react-app` with pnp, they have added a flag for it. The command: `npx create-react-app &lt;YOURaPPnAME&gt; --use-pnp` will create a brand new React App with pnp already enabled. To see if either of these worked check your package.json for 
`{
 "installConfig": {
 "pnp": true
 } 
}`

If it is there and your `.pnp.js`is generated then you have done everything you need to. Turning PnP off is as simple as deleting the file and removing the above code from your `package.json`.

Hopefully this has illuminated this particular topic for you. Consider trying out any PnP, tink, or anything else mentioned. As always if I have made a mistake please let me know, or if you have any suggestions for what I should write about next.