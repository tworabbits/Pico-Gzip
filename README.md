# Pico Gzip

Gzip plugin for [PicoCMS](https://github.com/picocms/Pico)

Use this plugin to enable gzip compression on your Pico responses. Prior to compressing the output, the browsers `Accept-Encoding` request header field is checked. In case gzip compression is supported and **not purposely** disabled via the `Gzip` page meta field, compression will be applied to the requested page.

# Requirements

The php `zlib` is required to run this plugin, which should be enabled by default in most php installations. In case `zlib` is not installed, PicoGzip will throw a `RuntimeException`. So it is safe to just give it a try.

# Installation

Copy `PicoGzip.php` to the plugins directory of your Pico installation and enable the plugin in your `config/config.php` file:
```
[...]
// Enable gzip compression plugin
$config['PicoGzip.enabled'] = true;
[...]
```

# Usage

By default, all pages will be compressed before they are sent back to the user. Use the `Gzip: false` header in any of your pages to disable compression.

```
---
Title: My post
Date: 2016-06-08
Description: This post will not be compressed
Gzip: false
---
```

You might want to adjust the compression level passed into [`gzencode`](http://php.net/manual/de/function.gzencode.php). To do so, set the `gzip_compression_level` parameter in your Pico `config/config.php` file:

```
[...]
// Gzip compression level, default to the highest (=9) if omitted
$config['gzip_compression_level'] = 5;
[...]
```