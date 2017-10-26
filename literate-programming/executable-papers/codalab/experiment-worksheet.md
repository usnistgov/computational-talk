## Author: Gael Varoquaux - License: BSD 3 clause

### Standard scientific Python imports

    import matplotlib.pyplot as plt

### Import datasets, classifiers and performance metrics

    from sklearn import datasets, svm, metrics
    
### The digits dataset

    digits = datasets.load_digits()
    
### The data that we are interested in is made of 8x8 images of digits, let's
### have a look at the first 4 images, stored in the `images` attribute of the
### dataset.  If we were working from image files, we could load them using
### matplotlib.pyplot.imread.  Note that each image must have the same size. For these
### images, we know which digit they represent: it is given in the 'target' of
## the dataset.

    images_and_labels = list(zip(digits.images, digits.target))
    for index, (image, label) in enumerate(images_and_labels[:4]):
        plt.subplot(2, 4, index + 1)
        plt.axis('off')
        plt.imshow(image, cmap=plt.cm.gray_r, interpolation='nearest')
        plt.title('Training: %i' % label)

### To apply a classifier on this data, we need to flatten the image, to
### turn the data in a (samples, feature) matrix:

    n_samples = len(digits.images)
    data = digits.images.reshape((n_samples, -1))

### Create a classifier: a support vector classifier

    classifier = svm.SVC(gamma=0.001)
    
### We learn the digits on the first half of the digits

    classifier.fit(data[:n_samples // 2], digits.target[:n_samples // 2])
    
### Now predict the value of the digit on the second half:

    expected = digits.target[n_samples // 2:]
    predicted = classifier.predict(data[n_samples // 2:])

    print("Classification report for classifier %s:\n%s\n"
      % (classifier, metrics.classification_report(expected, predicted)))
      
    print("Confusion matrix:\n%s" % metrics.confusion_matrix(expected, predicted))
    
% display contents /output.txt maxlines=100
[run run-python -- :train.py : python train.py]{0x3e8f7c43ff6c41a698d9327b054b379e}
    
### Preparing the plots

    images_and_predictions = list(zip(digits.images[n_samples // 2:], predicted))
    for index, (image, prediction) in enumerate(images_and_predictions[:4]):
        plt.subplot(2, 4, index + 5)
        plt.axis('off')
        plt.imshow(image, cmap=plt.cm.gray_r, interpolation='nearest')
        plt.title('Prediction: %i' % prediction)
        

    plt.show()
    
% display image /output.png
[run run-python -- :experiment.pkl,:experiment.pkl_01.npy,:experiment.pkl_02.npy,:experiment.pkl_03.npy,:experiment.pkl_04.npy,:experiment.pkl_05.npy,:experiment.pkl_06.npy,:experiment.pkl_07.npy,:experiment.pkl_08.npy,:experiment.pkl_09.npy,:experiment.pkl_10.npy,:predict.py : python predict.py]{0xb20e7dc772914c2f85aa24c7046ff793}

[dataset train.py]{0x9567437ae8ca44ec809b943786fe3a27}
[run run-python -- :train.py : python train.py]{0x3e8f7c43ff6c41a698d9327b054b379e}
[dataset experiment.pkl]{0x9926c6542dcd4f3aa89f38842b38ea54}
[dataset experiment.pkl_01.npy]{0x71028cc8e0414fe4835818541c0dc0e2}
[dataset experiment.pkl_02.npy]{0xd1992f1b5992486285e1ee3993c8d8a5}
[dataset experiment.pkl_03.npy]{0xa7d7b705766f4af5b65b1f9970372e3a}
[dataset experiment.pkl_04.npy]{0x0e4ca0d7d8ad4b1b9adb935edb8f3688}
[dataset experiment.pkl_05.npy]{0x7df65255ad4f408abb098f8206176922}
[dataset experiment.pkl_06.npy]{0x0b0b453a967e440bb80b510fad9597f5}
[dataset experiment.pkl_07.npy]{0x8b95f4492b75475792eb14a7ac84b95d}
[dataset experiment.pkl_08.npy]{0x209b03f206504af2a170ec5e36c5f32c}
[dataset experiment.pkl_09.npy]{0xae682c17a7aa4b138c98b482e09624d5}
[dataset experiment.pkl_10.npy]{0x17761bb432d345f7946948710d3cf0be}
[dataset predict.py]{0xea2ab3c6c9814e8aa8207d3594e94c81}
[run run-python -- :experiment.pkl,:experiment.pkl_01.npy,:experiment.pkl_02.npy,:experiment.pkl_03.npy,:experiment.pkl_04.npy,:experiment.pkl_05.npy,:experiment.pkl_06.npy,:experiment.pkl_07.npy,:experiment.pkl_08.npy,:experiment.pkl_09.npy,:experiment.pkl_10.npy,:predict.py : python predict.py]{0xb20e7dc772914c2f85aa24c7046ff793}