# Simpler human-readable labels for ImageNet [![Build Status](https://github.com/anishathalye/imagenet-simple-labels/workflows/CI/badge.svg)](https://github.com/anishathalye/imagenet-simple-labels/actions?query=workflow%3ACI)


The file [imagenet-simple-labels.json](imagenet-simple-labels.json) contains
simple, short, human-readable labels for the 1000 [ImageNet] classes.

There are similar files out there with human-readable labels for ImageNet
classes (see below for a comparison). The goal of this project is to have
simple, short, human-readable, and meaningful labels, _without being restricted
to choosing one of the synonyms out of the synset for each ImageNet class_.
These label names were chosen by looking at the synset for each ImageNet class
and either choosing one of the synonyms or choosing a new description
altogether, based on a couple guiding principles:

- Using Wikipedia or Google Search for canonicalization
- Preferring American English over British English
- Preserving genericized trademarks (e.g. keeping "Band-Aid" rather than
  replacing it with "adhesive bandage")

**Depending on your use case, this may or may not be for you.** If you're
looking for more "official" labels (such as those that always choose synonyms
out of the synsets rather than sometimes using new descriptions), consider some
of the alternatives compared below.

## Comparison

- **ImageNet** original labels. Each of the 1000 [ImageNet] classes corresponds
  to a [WordNet] synset (a set of synonyms). These are the "official" labels.
  [Here][imagenet-labels] is a file with a mapping of class IDs to these
  labels.
- **Keras** labels. [Keras][Keras] [uses][keras-imagenet-utils] this
  [data][keras-labels] for its human-readable labels. The labels consist of the
  first synonym from each synset (with spaces replaced with underscores).

Below is a table comparing ImageNet labels and Keras labels with our labels.
The table contains hand-picked examples to illustrate differences.

| ID | ImageNet | Keras | Simple (this repo) |
| --- | --- | --- | --- |
| 87 | African grey, African gray, Psittacus erithacus | African_grey | grey parrot |
| 97 | drake | drake | duck |
| 134 | crane | crane | crane (bird) |
| 156 | Blenheim spaniel | Blenheim_spaniel | King Charles Spaniel |
| 383 | Madagascar cat, ring-tailed lemur, Lemur catta | Madagascar_cat | ring-tailed lemur |
| 439 | bearskin, busby, shako | bearskin | military cap |
| 517 | crane | crane | crane (machine) |
| 628 | liner, ocean liner | liner | ocean liner |
| 667 | mortarboard | mortarboard | square academic cap |
| 699 | panpipe, pandean pipe, syrinx | panpipe | pan flute |
| 913 | wreck | wreck | shipwreck |
| 930 | French loaf | French_loaf | baguette |

## Usage

Below is a Python code sample showing how the label data can be used.

```python
import json

with open('imagenet-simple-labels.json') as f:
    labels = json.load(f)

def class_id_to_label(i):
    return labels[i]

print(class_id_to_label(924)) # prints "guacamole"
```

## License

Public domain.

[ImageNet]: http://www.image-net.org/
[WordNet]: https://wordnet.princeton.edu/
[imagenet-labels]: https://gist.github.com/yrevar/942d3a0ac09ec9e5eb3a
[Keras]: https://keras.io/
[keras-imagenet-utils]: https://github.com/keras-team/keras-applications/blob/master/keras_applications/imagenet_utils.py
[keras-labels]: https://s3.amazonaws.com/deep-learning-models/image-models/imagenet_class_index.json
