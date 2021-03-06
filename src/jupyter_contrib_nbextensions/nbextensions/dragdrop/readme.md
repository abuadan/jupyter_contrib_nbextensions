This IPython notebook extension allows dragging&dropping images from the desktop or other programs into a notebook. A new markdown cell is created below the currently selected cell and the image is embedded.
The notebook has been tested with Firefox and Chrome.

A demo video showing drag&drop of images is here:
http://youtu.be/buAL1bTZ73c


Internals
=========

The image will be uploaded to the server into the directory where your notebook resides. This means, the image is not copied into the notebook itself, it will only be linked to. The markdown cell in the notebook will contain this tag:

```html
<img  src="http://127.0.0.1:8888/notebooks/myimage.png"/>
```

If you run `nbconvert` to generate a HTML file, this image will remain outside of the html file. You can embedd all images by calling `nbconvert` with the option `--post=embed.EmbedPostProcessor`. The file `embed.py`, located in the same directory of this extension needs to be in `PYTHONPATH` to be found.