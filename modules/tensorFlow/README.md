﻿# TensorFlow.js

This module shows how to use any TensorFlow.js model in Custom Module on the example of [toxicity model](https://github.com/tensorflow/tfjs-models/tree/master/toxicity).

First, go to https://www.tensorflow.org/js/models and find a model that you would like to use in your Custom Module. Follow the instructions in the model's documentation.

## Installation

You will need to install the libraries with npm:

```bash
npm install @tensorflow/tfjs @tensorflow-models/toxicity
```

## Usage

You can use this template to create a Custom Module for cognigy.

1. Import your model using `require('@tensorflow-models/toxicity')` and create a function based on the model's documentation.

2. In order to get the text message from IFlowInput, use `input.input.text`. Then, you can apply model's functions on your input.

3. You can store the results in the Context or Input Object under the name given in the node's settings.
```	bash
	if (args.writeToContext) input.context.getFullContext()[args.store] = result;
	else input.input[args.store] = result;
```

4. Creating yout package.json, remember to include
```	bash
"scripts": {
		"build": "tsc -p .",
		"zip": "npm run build && zip test.zip build/* package.json package-lock.json README.md icon.png icon-large.png"
	},
```

5. Then, you can create a test.zip with all necessary files with
```bash
npm run zip
```
from your terminal.

You can find more informations about creating Custom Module in cognigy [docs](https://docs.cognigy.com/docs/integration-framework).


## TensorFlow to JavaScript

It is possible to convert any TensorFlow SavedModel, TensorFlow Hub module, Keras HDF5 or tf.keras SavedModel into TensorFlow.js. In order to do that follow the steps described [here](https://github.com/tensorflow/tfjs/tree/master/tfjs-converter).
