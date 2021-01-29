[![Latest stable version]][packagist] [![Total downloads]][packagist] [![License]][packagist] [![GitHub forks]][fork] [![Donate Paypal]][paypal] [![Wishlist amazon]][amazon] [![GitHub stars]][stargazers] [![GitHub watchers]][subscription] [![GitHub followers]][followers] [![Follow Jon on Twitter]][twitter]

# Jonnitto.PrettyEmbedVideo

Prettier embeds for your native videos in [Neos CMS] - with nice options like high-res preview images, lightbox feature, captions, and advanced customization of embed options.

![Screenshot]
![Screenshot with captions]

| Version | Neos                  | Maintained |
| ------- | --------------------- | :--------: |
| 1.\*    | ^4.2.\* + 5.\*        |            |
| 2.\*    | ^4.2.\* + 5.\*        |            |
| 3.\*    | ^4.2.\* + 5.\* + 7.\* |      ✓     |

## Installation

Most of the time, you have to make small adjustments to a package (e.g., configuration in `Settings.yaml`). Because of that, it is important to add the corresponding package to the composer from your theme package. Mostly this is the site package located under `Packages/Sites/`. To install it correctly go to your theme package (e.g.`Packages/Sites/Foo.Bar`) and run following command:

```bash
composer require jonnitto/prettyembedvideo --no-update
```

The `--no-update` command prevent the automatic update of the dependencies. After the package was added to your theme `composer.json`, go back to the root of the Neos installation and run `composer update`. Et voilà! Your desired package is now installed correctly.

## PrettyEmbedCollection

This package is member of the [PrettyEmbedCollection] which contains following packages:

- [PrettyEmbedVideo]
- [PrettyEmbedVimeo]
- [PrettyEmbedYoutube]

If you install the PrettyEmbedCollection the video players get grouped into an own group in the node-inspector; otherwise, they will be in the default group.

## FAQ

**What are the differences from the PrettyEmbed series to [Jonnitto.Plyr]?**

|                                    | PrettyEmbed series |  Plyr  |
| ---------------------------------- | :----------------: | :----: |
| YouTube Video                      |         ✓          |   ✓    |
| YouTube Playlist                   |         ✓          |        |
| Vimeo                              |         ✓          |   ✓    |
| Native Audio                       |         ✓          |   ✓    |
| Native Video                       |         ✓          |   ✓    |
| Advanced captions for native video |         ✓          |        |
| Preview image                      |         ✓          |        |
| Lightbox included                  |         ✓          |        |
| Preview image (for videos)         |         ✓          |        |
| Javascript API                     |                    |   ✓    |
| Filesize (JS & CSS)                |      smaller       | bigger |

All packages from the PrettyEmbed series have the benefit of a better frontend performance since the player gets only loaded on request. So, no iframe/video gets loaded until the user wants to watch a video.

## Customization

### Configuration

If you want to customize the default settings, take a look at the [Settings.Jonnitto.yaml] file. If no node property is giving, these default values will be taken. If you, for example, don't want to let the editor choose if the video should open in a lightbox you can deactivate the mixin in your Configuration folder like this:

```yaml
'Jonnitto.PrettyEmbedVideo:Content.Video':
  superTypes:
    'Jonnitto.PrettyEmbedHelper:Mixin.Lightbox': false
```

These are the available mixins used for the video:

| Mixin name (Prefix: `Jonnitto.PrettyEmbed`) | Description                                                      | Default value | Enabled per default |
| ------------------------------------------- | ---------------------------------------------------------------- | :-----------: | :-----------------: |
| `Helper:Mixin.Groups`                       | Enables the inspector groups                                     |               |          ✓          |
| `Helper:Mixin.IncludeAssets`                | Include the frontend resources                                   |               |          ✓          |
| `Video:Mixin.Sources`                       | Includes the properties for external and internal sources        |               |          ✓          |
| `Video:Collection.Track`                    | Include the possibility to set tracks to the video               |               |          ✓          |
| `Helper:Mixin.Image`                        | Add the preview image property                                   |               |          ✓          |
| `Helper:Mixin.Lightbox`                     | Open the video in a lightbox                                     |    `false`    |          ✓          |
| `Helper:Mixin.Title`                        | Set the title for easily identify the video in the content tree. |               |          ✓          |
| `Helper:Mixin.Loop`                         | Loop the video                                                   |    `false`    |                     |
| `Helper:Mixin.Controls`                     | Show the controls                                                |    `true`     |                     |
| `Helper:Mixin.Autoplay`                     | Autoplays the video,                                             |    `false`    |                     |
| `Helper:Mixin.Muted`                        | Mutes the video                                                  |    `false`    |                     |

If you want to use only internal or only external sources, you have to disable the supertype [`Jonnitto.PrettyEmbedVideo:Mixin.Sources`] and enable [`Jonnitto.PrettyEmbedVideo:Mixin.Assets`] (internal sources) or [`Jonnitto.PrettyEmbedVideo:Mixin.ExternalSources`] (external sources)

[`Jonnitto.PrettyEmbedVideo:Collection.Track`] adds the possability to add [`Jonnitto.PrettyEmbedVideo:Content.Track`] for subtitles, captions, descriptions, chapters or metadata.

### Fusion

If you want to use the player as a pure component, you can use the [`Jonnitto.PrettyEmbedVideo:Component.Video`] fusion prototype.

If you want to read the node properties and let the package handle all for you, you should use the [`Jonnitto.PrettyEmbedVideo:Content.Video`] prototype. For easier including in your node types, you can disable the content element wrapping with `contentElement = false`. This is useful if you want to create, for example, a text with a video node type.

[packagist]: https://packagist.org/packages/jonnitto/prettyembedvideo
[latest stable version]: https://poser.pugx.org/jonnitto/prettyembedvideo/v/stable
[total downloads]: https://poser.pugx.org/jonnitto/prettyembedvideo/downloads
[license]: https://poser.pugx.org/jonnitto/prettyembedvideo/license
[github forks]: https://img.shields.io/github/forks/jonnitto/Jonnitto.PrettyEmbedVideo.svg?style=social&label=Fork
[donate paypal]: https://img.shields.io/badge/Donate-PayPal-yellow.svg
[wishlist amazon]: https://img.shields.io/badge/Wishlist-Amazon-yellow.svg
[amazon]: https://www.amazon.de/hz/wishlist/ls/2WPGORAVYF39B?&sort=default
[paypal]: https://www.paypal.me/Jonnitto/20eur
[github stars]: https://img.shields.io/github/stars/jonnitto/Jonnitto.PrettyEmbedVideo.svg?style=social&label=Stars
[github watchers]: https://img.shields.io/github/watchers/jonnitto/Jonnitto.PrettyEmbedVideo.svg?style=social&label=Watch
[github followers]: https://img.shields.io/github/followers/jonnitto.svg?style=social&label=Follow
[follow jon on twitter]: https://img.shields.io/twitter/follow/jonnitto.svg?style=social&label=Follow
[twitter]: https://twitter.com/jonnitto
[fork]: https://github.com/jonnitto/Jonnitto.PrettyEmbedVideo/fork
[stargazers]: https://github.com/jonnitto/Jonnitto.PrettyEmbedVideo/stargazers
[subscription]: https://github.com/jonnitto/Jonnitto.PrettyEmbedVideo/subscription
[followers]: https://github.com/jonnitto/followers
[license]: LICENSE
[neos cms]: https://www.neos.io
[prettyembedcollection]: https://github.com/jonnitto/Jonnitto.PrettyembedCollection
[prettyembedvideo]: https://github.com/jonnitto/Jonnitto.PrettyEmbedVideo
[prettyembedvimeo]: https://github.com/jonnitto/Jonnitto.PrettyEmbedVimeo
[prettyembedyoutube]: https://github.com/jonnitto/Jonnitto.PrettyEmbedYoutube
[jonnitto.plyr]: https://github.com/jonnitto/Jonnitto.Plyr
[settings.jonnitto.yaml]: Configuration/Settings.Jonnitto.yaml
[`jonnitto.prettyembedvideo:component.video`]: Resources/Private/Fusion/Component/Video.fusion
[`jonnitto.prettyembedvideo:content.video`]: Resources/Private/Fusion/Content/Video.fusion
[`jonnitto.prettyembedvideo:mixin.sources`]: Configuration/NodeTypes.Mixin.Sources.yaml
[`jonnitto.prettyembedvideo:mixin.assets`]: Configuration/NodeTypes.Mixin.Assets.yaml
[`jonnitto.prettyembedvideo:mixin.externalsources`]: Configuration/NodeTypes.Mixin.ExternalSources.yaml
[`jonnitto.prettyembedvideo:collection.track`]: Configuration/NodeTypes.Collection.Track.yaml
[`jonnitto.prettyembedvideo:content.track`]: Configuration/NodeTypes.Content.Track.yaml
[screenshot]: https://user-images.githubusercontent.com/4510166/76709933-3fbaf000-6703-11ea-8281-007d48174992.png
[screenshot with captions]: https://user-images.githubusercontent.com/4510166/76709937-447fa400-6703-11ea-9793-4eec0c7fb90f.png
