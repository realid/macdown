# MacDown

[![](https://img.shields.io/github/release/realid/macdown.svg)](https://github.com/realid/macdown/releases/latest)
![Total downloads](https://img.shields.io/github/downloads/realid/macdown/latest/total.svg)


MacDown is an open source Markdown editor for macOS, released under the MIT License. The author stole the idea from [Chen Luo](https://twitter.com/chenluois)’s [Mou](http://mouapp.com) so that people can make crappy clones.

Download current builds from the [GitHub Releases](https://github.com/realid/macdown/releases/latest) page.

## Install

[Download the latest release](https://github.com/realid/macdown/releases/latest), unzip it, and drag the app to Applications.

Current release builds in this fork target macOS 11.0 and newer and include Apple Silicon native binaries.

MacDown is also available through Homebrew:

    brew install --cask macdown

Note: the Homebrew cask may track upstream MacDown releases instead of this fork.

## Screenshot

![screenshot](assets/screenshot.png)

## License

MacDown is released under the terms of MIT License. You may find the content of the license [here](http://opensource.org/licenses/MIT), or inside the `LICENSE` directory.

You may find full text of licenses about third-party components in the `LICENSE` directory, or the **About MacDown** panel in the application.

The following editor themes and CSS files are extracted from [Mou](http://mouapp.com), courtesy of Chen Luo:

* Mou Fresh Air
* Mou Fresh Air+
* Mou Night
* Mou Night+
* Mou Paper
* Mou Paper+
* Tomorrow
* Tomorrow Blue
* Tomorrow+
* Writer
* Writer+
* Clearness
* Clearness Dark
* GitHub
* GitHub2

## Development

This fork has been updated to build as a native Apple Silicon app on modern macOS.

### Requirements

If you wish to build MacDown yourself, you will need the following components/tools:

* Full Xcode with the macOS SDK (Apple Silicon native builds require Xcode.app, not just the Command Line Tools)
* Git
* A separate Ruby environment plus [Bundler](http://bundler.io)

> Note: Do not rely on the system Ruby for CocoaPods. Use a separate Ruby installation and run CocoaPods through Bundler.

> Note: Old versions of CocoaPods are not supported. Please use Bundler to execute CocoaPods, or make sure your CocoaPods is at least as new as the version shown in `Gemfile.lock`.

> Note: The active developer directory must point to the full Xcode app when building the macOS targets. If `xcodebuild` reports that only the Command Line Tools are selected, switch with:
>
>     sudo xcode-select -s /Applications/Xcode.app/Contents/Developer
>
> and then retry.

MacDown now targets macOS 11.0 and newer for Apple Silicon native builds.

### Environment Setup

After cloning the repository, run the following commands inside the repository root (directory containing this `README.md` file):

    git submodule update --init
    bundle install
    bundle exec pod install
    make -C Dependency/peg-markdown-highlight

Then open `MacDown.xcworkspace` in Xcode. The first command initialises the dependency submodule(s) used in MacDown; the second one installs dependencies managed by CocoaPods.

For command-line builds, a typical release build looks like:

    xcodebuild -workspace MacDown.xcworkspace -scheme MacDown -configuration Release -sdk macosx -arch arm64 build

Refer to the official guides of Git and CocoaPods if you need more instructions. If you run into build issues later on, try running the following commands to update dependencies:

    git submodule update
    bundle exec pod install

### Translation

Please help translation on [Transifex](https://www.transifex.com/macdown/macdown/).

![Transifex translation percentage](https://www.transifex.com/projects/p/macdown/resource/macdownxliff/chart/image_png/)

## Discussion

[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/realid/macdown)

Join our [Gitter channel](https://gitter.im/realid/macdown) if you have any problems with MacDown. Any suggestions are welcomed, too!

You can also [file an issue directly](https://github.com/realid/macdown/issues/new) on GitHub if you prefer so. But please, **search first to make sure no-one has reported the same issue already** before opening one yourself. MacDown does not update in your computer immediately when we make changes, so something you experienced might be known, or even fixed in the development version.

MacDown depends a lot on other open source projects, such as [Hoedown](https://github.com/hoedown/hoedown) for Markdown-to-HTML rendering, [Prism](http://prismjs.com) for syntax highlighting (in code blocks), and [PEG Markdown Highlight](https://github.com/ali-rantakari/peg-markdown-highlight) for editor highlighting. If you find problems when using those particular features, you can also consider reporting them directly to upstream projects as well as to MacDown’s issue tracker. I will do what I can if you report it here, but sometimes it can be more beneficial to interact with them directly.
