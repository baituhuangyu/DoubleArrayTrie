
forked from https://github.com/yanwii/DoubleArrayTrie


## DoubleArrayTrie

DoubleArrayTrie(DAT) support prefix search & exact search & multiple pattern match for python implemented by c++

### What's different

Now greedy search is supported:  
function `search` only returns the longest subsequence(greedy search)
function `maximum_search` returns all subsequences  

    
    word: she sher shers he
    to_search: shers
    
    search: 
    {'entities': [{'begin': 0, 'end': 5, 'entity': 'shers'}]}
    
    maximum_search: 
    {'entities': [{'begin': 0, 'end': 3, 'entity': 'she'}, {'begin': 0, 'end': 4, 'entity': 'sher'}, {'begin': 0, 'end': 5, 'entity': 'shers'}, {'begin': 1, 'end': 3, 'entity': 'he'}]}

## platform

  | python | OS | status |
  | ----- | ---- | ---- |
  | ubuntu | python2 | ok |
  | ubuntu | python3 | ok |
  | macos | python3.7 | ok |


### C++

    #include "double_array_trie.h"
    
    DoubleArrayTrie dat;
    // load from file
    dat.load_file("test.txt")
    // or add word
    dat.add_word("he")
    dat.add_word("she")
    // make base & check
    dat.make()
    // greedy_search
    vector<string> index_s = dat.search("ushers")
    // maximum_search
    vector<string> index_s = dat.maximum_search("ushers")

### Python

    # install 
    pip install pydat

    # use
    dat = pydat.Dat()
    dat.load_file("test.txt")
    dat.add_word("he")
    dat.make()
    # search
    dat.search("ushers")
    # greedy_search
    dat.maximum_search("ushers")


### About DAT
![](https://linux.thai.net/~thep/datrie/double.gif)

**Definition**  
check[base[s] + c] = s  
base[s] + c = t  


Reference: [An implementation of Double-Array Trie](https://linux.thai.net/~thep/datrie/datrie.html#Double)

### install step
#### For most, run cmd below.
-  libboost_python37 boost version 1_73_0

- git clone https://github.com/baituhuangyu/DoubleArrayTrie.git

- python setup install

#### build `new` libboost_python
- Should ignore this part for most.

- If you need to build `new` libboost_python for your `new` env/os/python.

- 1. build libboost_python, like this:

- step 1) run bootstrap.sh, configure

./bootstrap.sh \
--prefix=./build/ \
--with-libraries=python \
--with-python=/PATH/TO/bin/python \
--with-python-root=/PATH/TO/PYTHON_ROOT/ \
--with-python-version=3.7

- step 2) build

./b2 install --prefix=./build/

- step 3) copy files

cp build/lib/libboost_python37.dylib /PATH/TO/YOUR/DoubleArrayTriepydat/pydat/

cp build/lib/libboost_python37.dylib /PATH/TO/YOUR/DoubleArrayTrie/pydat/pydat/

#rm -rf /PATH/TO/YOUR/DoubleArrayTrie/pydat/include/

cp build/include/ /PATH/TO/YOUR/DoubleArrayTrie/pydat/include/

- step 4) build & install pydat


### 2020.07.30
- support macos
- fix can't find libboost_python3.dylib on Darwin platform

### Update Log

#### 2018.09.19
- optimize the algorithm

#### 2018.08.29
- support greedy_search

#### 2018.08.08 
- support python3