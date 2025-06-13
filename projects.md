---
title: Holland Reece Brown
layout: default
---


# Selected Projects
## Analyzing high-dimensional, multi-modal data in healthcare and clinical research
- As a computational research assistant, I analyzed high-dimensional datasets of brain images, cognitive tests and psychiatric evaluations to inform therapeutic development for psychiatric disorders.

- Building on code developed by other research groups, I developed a [preprocessing pipeline](https://github.com/holland-reece/SE-fMRI-Pipeline-magnitude-fieldmaps) for human brain imaging data, incorporating machine learning-based denoising tools to clarify images and understand how different clinical populations' brain scans change over time.

- In a cross-institutional collaboration, I applied my experience with human health data to develop analysis scripts for a study in zebrafish larvae.
> Velez-Angel, 2024, [*bioRxiv*](https://doi.org/10.1101/2025.02.07.637118)
<br>

---

## AI Applications
- In a cross-functional team, I helped train a variational autoencoder deep learning model to better understand visual processing in people with schizophrenia. Using brain images as input, the model created feature maps it used to reconstruct photographs study participants viewed during the brain scan.

<img src="images/vae_results.png" alt="VAE" width="600">

- Fitting deep learning models on the MNIST publicly available dataset (ML master's course project)
    - I demonstrate [tuning model parameters](https://github.com/holland-reece/neural-network-fitting-demo) (number and type of network layers, number of epochs, learning rate and type of optimizer) to fit a neural network, then evaluate and compare model performance.

```python
model.summary()

# define loss function
loss_fn = tf.keras.losses.CategoricalCrossentropy(
    from_logits=True, name='categorical_crossentropy')

# define optimizer,loss function and evaluation metric
optimizer = tf.keras.optimizers.Adam(lr = 0.1) # change learning rate
model.compile(optimizer=optimizer,
             loss=loss_fn,
             metrics=['accuracy'])

# train the model
model.fit(x_train_small, y_train_small_onehot,epochs=5)

# evaluate model
y_test_onehot = to_categorical(y_test)
model.evaluate(x_test,y_test_onehot,verbose=2)
```

### I choose the best model for a dataset, fit it, fine-tune it, and validate it to solve data science problems effectively and efficiently.

- I compared [lasso and ridge regression techniques](https://github.com/holland-reece/ridge-vs-lasso-reg) using k-fold cross validation and forward feature selection performed a classification of MNIST data using a [logistic regression classifier](https://github.com/holland-reece/logreg-classifier-MNIST-demo).
