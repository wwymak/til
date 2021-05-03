# Save and load a tf.keras model using .h5

The default way of saving tensorflow models results in a folder with a saved_mode.pb file + assets and variables 
folders. This might be less desirable if you only want one model file to load easily. However, you can save the 
model as a h5 file using keras, but there are some caveats-- if you have defined a custom layer(s), you have to pass 
that in when you load the h5 file using the `custom_objects` argument.

E.g. in the below model, which makes use of a pretrained hub model and a custom head, if you save in .h5 format, you 
have to reload it like below:
```python
import tensorflow as tf
import tensorflow_hub as hub

class ReduceMeanLayer(tf.keras.layers.Layer):
    def __init__(self, axis=0, **kwargs):
        super(ReduceMeanLayer, self).__init__(**kwargs)
        self.axis = axis

    def call(self, input):
        return tf.math.reduce_mean(input, axis=self.axis)


model = tf.keras.models.load_model(saved_model_path, custom_objects={'ReduceMeanLayer': ReduceMeanLayer,
                                                                    'KerasLayer': hub.KerasLayer})
```