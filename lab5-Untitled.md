```python
import tensorflow as tf
print(tf.__version__)
```


```python
!pip install tflite-model-maker
```


```python

```


```python
import os
import numpy as np
import tensorflow as tf
assert tf.__version__.startswith('2')
from tflite_model_maker import model_spec
from tflite_model_maker import image_classifier
from tflite_model_maker.config import ExportFormat
from tflite_model_maker.config import QuantizationConfig
from tflite_model_maker.image_classifier import DataLoader
import matplotlib.pyplot as plt
```


```python
image_path=tf.keras.utils.get_file(
'flower_photos.tgz',
'https://storage.googleapis.com/download.tensorflow.org/example_images/flower_photos.tgz',
extract=True)
image_path=os.path.join(os.path.dirname(image_path),'flower_photos')
```


```python
data=DataLoader.from_folder(image_path)
train_data,test_data=data.split(0.9)
```


```python
model=image_classifier.create(train_data)
```


```python
loss,accuracy=model.evaluate(test_data)
```


```python
model.export(export_dir='.')
```


```python

```
