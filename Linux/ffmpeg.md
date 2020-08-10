# ffmpeg

[ffmpeg home page](https://www.ffmpeg.org)

FFmpeg is a complete, cross-platform solution to record,
convert and stream audio and video.
It includes libavcodec - the leading audio/video codec library.

## Synopsis

```sh
ffmpeg [global_options] \
    {[input_file_options] -i input_url} \
    ... \
    {[output_file_options] output_url} \
    ...
```


## Features

* Very fast video and audio converter
* grab from a live audio/video source
* convert between arbitrary smple rates and resize video on the fly with high quality polyhpase filter

## Usage

### Filtering

1. Simple filtergraphs
2. Complex filtergraphs

### Stream copy

It is useful for changing the container format or modifying container-level metadata.
