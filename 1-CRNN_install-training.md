Follow my steps directly

------

- ## install

  this is crnn_chinese_characters: https://github.com/Sierkinhane/crnn_chinese_characters_rec

  Reference  https://www.cnblogs.com/sierkinhane/p/9715582.html

```
conda create -n crnn_chinese_characters python=3.6
```

![1550935899380](img/1550935899380.png)

```
conda activate crnn_chinese_characters

cd crnn_chinese_characters
```

![1550935920835](img/1550935920835.png)

```
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple torch torchvision
```

![1550935944000](img/1550935944000.png)

![1550935984024](img/1550935984024.png)

```
pip install decorator cloudpickle>=0.2.1 dask[array]>=1.0.0 matplotlib>=2.0.0 networkx>=1.8 scipy>=0.17.0 bleach python-dateutil>=2.1 decorator
```

install warp-ctc: https://github.com/SeanNaren/Warp-ctc

```
unzip warp-ctc-pytorch_bindings.zip
cd warp-ctc
mkdir build; cd build
cmake ..
make
```

![1550936068675](img/1550936068675.png)

```
cd pytorch_binding
python setup.py install
```

![1550936101874](img/1550936101874.png)

- ## Test

![1550936614872](img/1550936614872.png)

- ## Training

  making our datasets

   Download 3.6 million Chinese datasets first  <https://pan.baidu.com/s/1ufYbnZAZ1q0AlK7yZ08cvQ>

  The corresponding label of the picture: https://pan.baidu.com/s/1jfAKQVjD-SMJSffOwGhh8A 密码：u7bo

  first. divide the datasets into train-datasets & val-datasets

  ```
  actually i use my own datasets，my datasets have 10 thousands and 50 hundreds，so。。
  i divide these images into two folders：train & val
  i divide the labels.txt into two folders：train.txt & val.txt
  ```

  ```
  train folder：including 10 thousands image and the train.txt
  val folder：including 50 hundreds image and the val.txt
  ```

  ![1555052107277](img/1555052107277.png)

  The next step is to make data in lmdb format.

  ```
  create a new folder：lmdb
  under the lmdb folder：create two folders：train & val 
  ```

  Modify the corresponding contents in the **tolmdb.py**，as a result ，generate .mdb files

  Modify twice the path，corresponding **train** & **val**

  ![1555052789582](img/1555052789582.png)

  run twice

  ```
  python2 tolmdb.py  #note：must be python2
  ```

  ![1555052548976](img/1555052548976.png)

  and then....training

  The path of **train's .mdb** files & **val's .mdb files**

  ```
  python crnn_main.py --trainroot lmdb_dataset/nu1/lmdb/train/ --valroot lmdb_dataset/nu1/lmdb/val/ --cuda
  ```

  ![1550938449295](img/1550938449295.png)

![1550938459774](img/1550938459774.png)5