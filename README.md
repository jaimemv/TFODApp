# TensorFlow JS

Real time object detection using TensorFlow Object Detection API, React and TensorFlow JS.

# 1. Install node.js

Install through the website [https://nodejs.org/en/](https://nodejs.org/en/) and install the dependencies through `npm` (package manager similar to pip in python).

The following line creates the directory `node_modules` where the dependencies will be stored.

```bash
npm install
```

![Untitled](TensorFlow%20JS%20969029ccaa9b40539b95886b601f1d0e/Untitled.png)

# 2. Create object storage repository on IBM Cloud

Upload the files of TFJS Model previously exported. It can be found on `/Users/jaime/deep_learning/object_detection_tf/Tensorflow/workspace/models/my_ssd_mobnet/tfjsexport`

![Untitled](TensorFlow%20JS%20969029ccaa9b40539b95886b601f1d0e/Untitled%201.png)

Enable the public access:

![Untitled](TensorFlow%20JS%20969029ccaa9b40539b95886b601f1d0e/Untitled%202.png)

# 3. Place the model url on the `App.js`

Click on `model.json` that is the actual model and copy the path:

![Captura de pantalla 2021-10-28 a las 21.09.16.png](TensorFlow%20JS%20969029ccaa9b40539b95886b601f1d0e/Captura_de_pantalla_2021-10-28_a_las_21.09.16.png)

And place on `const net = await tf.loadGraphModel("http://...")`

![Captura de pantalla 2021-10-28 a las 21.08.01.png](TensorFlow%20JS%20969029ccaa9b40539b95886b601f1d0e/Captura_de_pantalla_2021-10-28_a_las_21.08.01.png)

# 4. Download the IBM Cloud client and Object Store plugin

Download the client through the following link [https://github.com/IBM-Cloud/ibm-cloud-cli-release](https://github.com/IBM-Cloud/ibm-cloud-cli-release).

Once we have the client, run the following line ([https://cloud.ibm.com/docs/cli?topic=cli-install-devtools-manually](https://cloud.ibm.com/docs/cli?topic=cli-install-devtools-manually)):

```bash
ibmcloud plugin install cloud-object-storage
```

Then login with the following line. Place the name of your bucket (is globally unique). It will ask for your user and password (The same of your IBM Cloud account):

```bash
ibmcloud cos bucket-cors-put --bucket directionstfodjaime --cors-configuration file://corsconfig.json
```

# 5. Start the app

The following code should initialize the web app on localhost:

```bash
npm start
```

# 6. Tune the variables to get live predictions

In order to check which object should be placed in `boxes`, `classes` and `scores` let's print what the objects are:

```jsx
console.log(await obj[0].array())
```

![Untitled](TensorFlow%20JS%20969029ccaa9b40539b95886b601f1d0e/Untitled%203.png)

We should try one at a time, save and refresh the page to check what is being outputted in console.


![Untitled](TensorFlow%20JS%20969029ccaa9b40539b95886b601f1d0e/Untitled%204.png)

Note how the shapes of the objects should have the following shapes:

![Captura de pantalla 2021-10-28 a las 13.34.15.png](TensorFlow%20JS%20969029ccaa9b40539b95886b601f1d0e/Captura_de_pantalla_2021-10-28_a_las_13.34.15.png)
