Assume that you are working on an image classification problem using Deep Learning in Tensorflow and your image dataset is split into subfolders,
each subfolder named after a class and you do not wish to manually create training, testing and validation folders. If you are new to tensorflow 
and have been using the "tf.keras.preprocessing.image.ImageDataGenerator" to split your data into training and validation sets, then you may have
come across the problem where currently (in the recent version of TF v2.13.0 as of August 2023) you can not use the same method to split the data into train, validation and 
test sets i.e., if your dataset path is in "data_root" and if you use the following code,

valid_generator = valid_datagen.flow_from_directory( data_root,
subset="validation", 
shuffle=True, 
target_size=IMAGE_SHAPE, )

then you can set subset="validation" or subset="training" but you can not use subset="testing" as it is not currently supported in tensorfow. Which is
why I have created this simple code which can be used to split the image data in "valid_generator" further into validation and test sets. So in a nutshell,
you first split your data into train and validation sets. And then you further split the validation data into two halves, where the first half can be used 
for validation while the other half can be set aside for testing.
