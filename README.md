Vide
====

Easy as hell jQuery plugin for video backgrounds.

## Notes

* All modern desktop browsers are supported.
* IE9+

## Instructions

Download it from [GitHub](https://github.com/tete-chercheuse/vide/releases/latest) or via Bower:
`bower install tete-chercheuse/vide`

Include plugin: `<script src="js/jquery.vide.min.js"></script>`

Prepare your video in several formats like '.webm', '.mp4' for cross browser compatibility, also add a poster with `.jpg`, `.png` or `.gif` extension:
```
path/
├── to/
│   ├── video.mp4
│   ├── video.ogv
│   ├── video.webm
│   └── video.jpg
```

Add `data-vide-bg` attribute with a path to the video and poster without extension, video and poster must have the same name. Add `data-vide-options` to pass vide options, if you need it. By default video is muted, looped and starts automatically.
```html
<div style="width: 1000px; height: 500px;"
  data-vide-bg="path/to/video" data-vide-options="loop: false, muted: false, position: 0% 0%">
</div>
```

Also you can set extended path:
```html
<div style="width: 1000px; height: 500px;"
  data-vide-bg="mp4: path/to/video1, webm: path/to/video2, ogv: path/to/video3, poster: path/to/poster"
  data-vide-options="posterType: jpg, loop: false, muted: false, position: 0% 0%">
</div>
```

In some situations it can be helpful to initialize it with JS because Vide doesn't have mutation observers:
```js
$('#myBlock').vide('path/to/video');
$('#myBlock').vide('path/to/video', {
...options...
});
$('#myBlock').vide({
  mp4: path/to/video1,
  webm: path/to/video2,
  ogv: path/to/video3,
  poster: path/to/poster
}, {
...options...
});
$('#myBlock').vide('extended path as a string', 'options as a string');
```

Easy as hell.

## Options

Below is a complete list of options and matching default values:

```js
{
  volume: 1,
  playbackRate: 1,
  muted: true,
  loop: true,
  autoplay: true,
  position: '50% 50%', // Similar to the CSS `background-position` property.
  posterType: 'detect', // Poster image type. "detect" — auto-detection; "none" — no poster; "jpg", "png", "gif",... - extensions.
  resizing: true, // Auto-resizing, read: https://github.com/tete-chercheuse/vide#resizing
  bgColor: 'transparent', // Allow custom background-color for Vide div,
  className: '' // Add custom CSS class to Vide div
}
```

## Methods

Below is a complete list of methods:

```js
// Get instance of the plugin
var instance = $('#yourElement').data('vide');

// Get video element of the background. Do what you want.
instance.getVideoObject();

// Resize video background.
// It calls automatically, if window resize (or element, if you will use something like https://github.com/cowboy/jquery-resize).
instance.resize();

// Destroy plugin instance
instance.destroy();
```

## Resizing

The Vide plugin resizes if the window resizes. If you will use something like https://github.com/cowboy/jquery-resize, it will resize automatically when the container resizes. Or simply use `resize()` method whenever you need.

Set the `resizing` option to false to disable auto-resizing.

## Encoding video

http://diveintohtml5.info/video.html#miro
