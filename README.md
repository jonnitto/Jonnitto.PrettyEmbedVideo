[![Latest stable version]][packagist] [![Total downloads]][packagist] [![License]][packagist] [![GitHub forks]][fork] [![Donate Paypal]][paypal] [![Wishlist amazon]][amazon] [![GitHub stars]][stargazers] [![GitHub watchers]][subscription] [![GitHub followers]][followers] [![Follow Jon on Twitter]][twitter]

# Jonnitto.PrettyEmbedVideo

**For a detail guide, please visit the [PrettyEmbed Wiki](https://github.com/jonnitto/Jonnitto.PrettyEmbedHelper/wiki)**

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

Most of the time, you have to make small adjustments to a package (e.g., configuration in `Settings.yaml`). Because of
that, it is essential to add the corresponding package to the composer from your theme package. Navigate to this package
in your CLI and run the following command:

```bash
composer require jonnitto/prettyembedvideo --no-update
```

The `--no-update` command prevent the automatic update of the dependencies. After the package was added to your package
`composer.json`, go back to the root of the Neos installation and run `composer update`. Et voilà! Your desired package
is now installed correctly.

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
[prettyembedcollection]: https://github.com/jonnitto/Jonnitto.PrettyembedCollection
[prettyembedvideo]: https://github.com/jonnitto/Jonnitto.PrettyEmbedVideo
[prettyembedvideoplatforms]: https://github.com/jonnitto/Jonnitto.PrettyEmbedVideoPlatforms
[jonnitto.plyr]: https://github.com/jonnitto/Jonnitto.Plyr
[screenshot]: https://github.com/jonnitto/Jonnitto.PrettyEmbedVideo/assets/4510166/beb36d49-d274-4887-9ac3-89fde42e2cdf
