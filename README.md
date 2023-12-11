[![Latest stable version]][packagist] [![Total downloads]][packagist] [![License]][packagist] [![GitHub forks]][fork] [![Donate Paypal]][paypal] [![Wishlist amazon]][amazon] [![GitHub stars]][stargazers] [![GitHub watchers]][subscription] [![GitHub followers]][followers] [![Follow Jon on Twitter]][twitter]

# Jonnitto.PrettyEmbedVideo

Prettier embeds for your native videos in [Neos CMS] - with excellent options like high-res preview images, lightbox feature, captions, and advanced customization of embed options.

![Screenshot]

| Version | Neos           | Maintained |
| ------- | -------------- | :--------: |
| 1.\*    | ^4.2.\* + 5.\* |     ✗      |
| 2.\*    | ^4.2.\* + 5.\* |     ✗      |
| 3.\*    | ^4.2.\* + >= 5 |     ✗      |
| 4.\*    | >= 5.3         |     ✗      |
| 6.\*    | >= 7.3         |     ✓      |

> The version jump was made to have all packages from the PrettyEmbed series on the same number

## Installation

Most of the time, you have to make small adjustments to a package (e.g., a configuration in `Settings.yaml`). Thus, it is essential to add the corresponding package to the composer from your theme package. Mostly this is the site package located under `Packages/Sites/`. To install it correctly, go to your theme package (e.g.`Packages/Sites/Foo.Bar`) and run the following command:

```bash
composer require jonnitto/prettyembedvideo --no-update
```

The `--no-update` command prevent the automatic update of the dependencies. After the package was added to your theme `composer.json`, go back to the Neos installation's root and run `composer update`. Et voilà! Your desired package is now installed correctly.

## PrettyEmbedCollection

This package is member of the [PrettyEmbedCollection] which contains following packages:

- [PrettyEmbedVideo]
- [PrettyEmbedVideoPlatforms]

If you install the PrettyEmbedCollection, the video players get grouped into an own group in the node-inspector; otherwise, they will be in the default group.

## FAQ

**What are the differences between the PrettyEmbed series to [Jonnitto.Plyr]?**

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
| Javascript API                     |         ✓          |   ✓    |
| Filesize (JS & CSS)                |      smaller       | bigger |

All packages from the PrettyEmbed series benefit from a better frontend performance since the player gets only loaded on request. So, no iframe/video gets loaded until the user wants to watch a video.

## Customization

### Global settings for the whole PrettyEmbed series

The settings will be set globally from the [PrettyEmbedHelper] package. These are the default settings for videos:

```yaml
Jonnitto:
  PrettyEmbed:
    # Set this to true for debug output
    debug: false

    # If you have your own AlpineJS in your setup, you can disable the check here. Alpine must be an global variable
    includeAlpineJsCheck: true

    # If you want to use your own assets, set this to false
    includeAssets:
      css: true
      js: true

    # Can be `lazy`, `eager` or `null`
    loadImageStrategy: lazy

    # If this is set to a string, the element gets wrapped with a div and the class with the giving string.
    # If set to true, the element gets wrapped with a div without any class.
    # If set to false, the element get not wrapped at all
    wrapper: false

    # The buttons which get injected (file content) to the player.
    # You can also overwrite the button Fusion components
    button:
      play: "resource://Jonnitto.PrettyEmbedHelper/Public/Assets/PlayButton.svg"
      pause: "resource://Jonnitto.PrettyEmbedHelper/Public/Assets/PauseButton.svg"

    # This is the maximum width of a custom preview image
    maximumWidth: 1920

    Video:
      # If true, the browser will offer controls to allow the user to control
      # video playback, including volume, seeking, and pause/resume playback.
      controls: true

      # Should the video be opened on a lightbox? Per default this is set via the node properties
      lightbox: false

      # If true, the video automatically begins to play back as soon
      # as it can do so without stopping to finish loading the data.
      autoplay: false

      # If true, the browser will automatically seek back
      # to the start upon reaching the end of the video.
      loop: false

      # Whether the video is muted upon loading. Set automatically to true if autoplay is enabled
      muted: false

      # This enumerated attribute is intended to provide a hint to the browser about what
      # the author thinks will lead to the best user experience with regards to what content
      # is loaded before the video is played. It may have one of the following values:
      #  - none       Indicates that the video should not be preloaded.
      #  - metadata   Indicates that only video metadata (e.g. length) is fetched.
      #  - auto       Indicates that the whole video file can be downloaded, even if the user is not expected to use it
      preload: none

      # https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video#attr-crossorigin
      # anonymous || use-credentials || true || false
      crossorigin: false
```

If no node property is giving, these default values will be taken. If you, for example, don't want to let the editor
choose if the video should open in a lightbox, you can deactivate the mixin in your Configuration folder like this:

```yaml
"Jonnitto.PrettyEmbedVideo:Content.Video":
  superTypes:
    "Jonnitto.PrettyEmbedHelper:Mixin.Lightbox": false
```

These are the available mixins used for the video:

| Mixin name (Prefix: `Jonnitto.PrettyEmbed`) | Description                                                                                                          | Default value | Enabled per default |
| ------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | :-----------: | :-----------------: |
| `Helper:Mixin.Groups`                       | Enables the inspector groups                                                                                         |               |          ✓          |
| `Video:Mixin.Sources`                       | Includes the properties for external and internal sources                                                            |               |          ✓          |
| `Video:Collection.Tracks`                   | Include the possibility to set tracks to the video                                                                   |               |          ✓          |
| `Helper:Mixin.Image`                        | Add the preview image property                                                                                       |               |          ✓          |
| `Helper:Mixin.Lightbox`                     | Open the video in a lightbox                                                                                         |    `false`    |          ✓          |
| `Helper:Mixin.Title`                        | Set the title to identify the video in the content tree easily, and pass the title as `aria-label` to the component. |               |          ✓          |
| `Helper:Mixin.Loop`                         | Loop the video                                                                                                       |    `false`    |                     |
| `Helper:Mixin.Controls`                     | Show the controls                                                                                                    |    `true`     |                     |
| `Helper:Mixin.Autoplay`                     | Autoplays the video,                                                                                                 |    `false`    |                     |
| `Helper:Mixin.Muted`                        | Mutes the video                                                                                                      |    `false`    |                     |

If you want to use only internal or only external sources, you have to disable the supertype [`Jonnitto.PrettyEmbedVideo:Mixin.Sources`] and enable [`Jonnitto.PrettyEmbedVideo:Mixin.Assets`] (internal sources) or [`Jonnitto.PrettyEmbedVideo:Mixin.ExternalSources`] (external sources)

### Fusion

If you want to use the player as a pure component, you can use the `Jonnitto.PrettyEmbed:Presentation.Video` fusion prototype.

If you want to read the node properties and let the package handle all for you, you should use the `Jonnitto.PrettyEmbedVideo:Content.Video` prototype. For easier including in your node types, you can disable the content element wrapping with `contentElement = false`. This is useful if you want to create, for example, a text with a video node type.

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
[neos cms]: https://www.neos.io
[PrettyEmbedHelper]: https://github.com/jonnitto/Jonnitto.PrettyEmbedHelper
[prettyembedcollection]: https://github.com/jonnitto/Jonnitto.PrettyembedCollection
[prettyembedvideo]: https://github.com/jonnitto/Jonnitto.PrettyEmbedVideo
[prettyembedvideoplatforms]: https://github.com/jonnitto/Jonnitto.PrettyEmbedVideoPlatforms
[jonnitto.plyr]: https://github.com/jonnitto/Jonnitto.Plyr
[`jonnitto.prettyembedvideo:mixin.sources`]: NodeTypes/NodeTypes/Mixin/Sources.yaml
[`jonnitto.prettyembedvideo:mixin.assets`]: NodeTypes/NodeTypes/Mixin/Assets.yaml
[`jonnitto.prettyembedvideo:mixin.externalsources`]: NodeTypes/NodeTypes/Mixin/ExternalSources.yaml
[screenshot]: https://github.com/jonnitto/Jonnitto.PrettyEmbedVideo/assets/4510166/beb36d49-d274-4887-9ac3-89fde42e2cdf
