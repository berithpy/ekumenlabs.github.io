# Ekumenlabs.com - Dev Notes

---

## Optimization of Image assets

You should optimize any image asset you plan to use in the website. According to the guidelines of [Google's PageSpeed Insight](https://developers.google.com/speed/docs/insights/OptimizeImages), the following considerations must be made:

* Reduce quality to 85 if it was higher. With quality larger than 85, the image becomes larger quickly, while the visual improvement is little.
* Reduce Chroma sampling to 4:2:0, because human visual system is less sensitive to colors as compared to luminance.
* Use progressive format for images over 10k bytes. Progressive JPEG usually has higher compression ratio than baseline JPEG for large image, and has the benefits of progressively rendering.
* Use grayscale color space if the image is black and white.

This can be achieved quickly in the terminal using ImageMagick. You can install it with:

```
sudo apt-get install imagemagick
```

And then convert images with the following command:

```
convert -strip -quality 85 -sampling-factor 4:2:0 source-image output-image
```

* To resize the image, use `-resize WIDTHxHEIGHT`.
* To convert it to Progressive JPEG, include `-interlaced Plane`.
* To convert it to grayscale, include `-colorspace Gray/RGB`.

Notes:
* These are guidelines. You have to make sure the image looks good in the website.
* Resizing Black and White PNG files (client images) can lead to visual problems, such as the image looking pixelated or gray. You should always aim for the best look.

### Some image sizes

You should always check the HTML container and upload images to match their size. Some of the image sizes we are using are:

- Team pictures are 200x299 pixels.
- Client images should have a height of 40px.

---

## Middleman Information

When running `middleman`, you can navigate to `localhost:port/__middleman/` and see the [Sitemap](https://middlemanapp.com/advanced/sitemap/), [Configuration](https://middlemanapp.com/advanced/configuration/) and [Guides](https://middlemanapp.com/).

---

## Ignore Files

You can ignore to build something by adding to the `config.rb` file the following:
```
ignore "path/to/file"
```
Currently, we are ignoring the Blog section and its entries.
