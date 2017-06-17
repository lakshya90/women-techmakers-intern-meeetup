### TensorFlow Codelab

**Step 1 : Let’s check if TensorFlow is correctly installed.**

    import tensorflow as tf
    hello = tf.constant('Hello, TensorFlow!')
    sess = tf.Session() # It will print some warnings here.
    print(sess.run(hello))    #Output : Hello, TensorFlow!


**Step 2 : Retrieving the images**

    mkdir tf_files  #Creating a working directory
    cd tf_files

    curl -O http://download.tensorflow.org/example_images/flower_photos.tgz
    tar xzf flower_photos.tgz

    ls -l #Checking for flower_photos folder
    #Output : A folder named flower_photos inside which there are 5 sub folders namely daisy, tulips, sunflowers, roses and dandelion.

**Step 3 : (Re)training Inception**

    curl -O      https://raw.githubusercontent.com/tensorflow/tensorflow/r1.1/tensorflow/examples/image_retraining/retrain.py

    python retrain.py \
    --bottleneck_dir=bottlenecks \
    --how_many_training_steps=500 \
    --model_dir=inception \
    --summaries_dir=training_summaries/basic \
    --output_graph=retrained_graph.pb \
    --output_labels=retrained_labels.txt \
    --image_dir=flower_photos


**Step 4 : Using the Retrained Model**

    #Classifying an image
    curl -L https://goo.gl/3lTKZs > label_image.py

    #Run the python file on a daisy
    python label_image.py flower_photos/daisy/21652746_cc379e0eea_m.jpg

    #Output : 	daisy (score = 0.99071)
    #sunflowers (score = 0.00595)
    #dandelion (score = 0.00252)
    #roses (score = 0.00049)
    #tulips (score = 0.00032)
      
**Step 5 : Going above and beyond!**

#Trying Other Hyperparameters
--learning_rate = 0.005(more time, high precision)[Default : 0.01]

#Training on Your Own Categories
--image_dir=<root folder containing subfolders having folder names as label names, and the images inside each folder should be pictures that correspond to that label>

* NOTE : You can find the entire code at https://github.com/lakshya90/women-techmakers-intern-meeetup/ *
      

Feedback form : https://goo.gl/forms/XRkcKwApgrqjtZcG2



