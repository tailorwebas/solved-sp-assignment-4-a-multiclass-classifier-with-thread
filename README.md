Download Link: https://assignmentchef.com/product/solved-sp-assignment-4-a-multiclass-classifier-with-thread
<br>



<strong>1.Problem Description            </strong>

In assignment 4, you are required to implement a multiclass classifier with thread. You should train a model to classify handwritten digits from MNIST dataset. And the most important part is that you have to accelerate the matrix multiplication (let it parallelly) by thread.

In training, you should decide how many iterations you train your classifier on your own.

For each iteration, you update your classifier with：

<img decoding="async" data-recalc-dims="1" data-src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2020/05/197.png?w=980&amp;ssl=1" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2020/05/197.png?w=980&amp;ssl=1" data-recalc-dims="1">

 </noscript>

X：training data matrix (60000 * 784)

W：weight matrix (784 * 10)

<em><u>(If you consider adding bias to your classifier, you can let W to be 785*10, and add a column with 1’s to X.)</u></em>

y_hat：predicted label (60000 * 10)

y：true label, you need to transform each label to one-hot. (60000 * 10)

(if label = 2 =&gt; [0, 0, 1, 0, 0, 0, 0, 0, 0, 0])

lr：learning rate (scalar)

You need to create threads to accelerate the matrix multiplication in (1). We will tell you how many threads you should create, and each thread should calculate [60000 / thread_num] rows multiplication.

(For example, if thread_num = 1000, each thread should be responsible for “60” rows ([60*784] * [784*10]) multiplication in (1).)

To evaluate the accuracy, you may choose the label with largest probability from 10 classes for each image.

<ol start="2">

 <li><strong> Format of Inputs &amp; Outputs</strong></li>

</ol>

Input：MNIST dataset (including 4 files)

X_train：60000 images, 784 pixels for each image, value：0~255

y_train：60000 labels, value：0~9

X_test：10000 images

y_test：10000 labels

data link : <strong><u><a href="https://drive.google.com/drive/folders/1wips8uJtKFIlnXVzu2fDC_SRjbxaxiD2?usp=sharing">https://drive.google.com/drive/folders/1wips8uJtKFIlnXVzu2fDC_SRjbxaxiD2?usp=sharing</a></u></strong>

Output：result.csv

format：

<strong><img decoding="async" data-recalc-dims="1" data-src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2020/05/869.png?w=980&amp;ssl=1" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

  <noscript>

   <img decoding="async" src="https://i0.wp.com/www.ankitcodinghub.com/wp-content/uploads/2020/05/869.png?w=980&amp;ssl=1" data-recalc-dims="1">

  </noscript>3.Sample Execution</strong>

./hw4 [X_train] [y_train] [X_test] [number of threads]

(compile：gcc hw4.c -lm -lpthread -O3 -o hw4)