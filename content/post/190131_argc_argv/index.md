---
title: "main文の引数 argc argv の動作確認 [C++]"
date: 2019-01-31T13:17:04+09:00
slug: argc-argv
draft: false

# post thumb
image: "logo.jpg"

# meta description
description: "C++のmain文の引数の動作確認です。Ubuntu 16.04 LTS での確認を行っています"

# taxonomies
categories:
  - "Programming"
tags:
  - "C++"

# post type
type: "post"
---

# はじめに

OSは``Ubuntu 16.04 LTS``です。

``int main(int argc, char* argv[])``の引数の挙動を確かめます。

``argc``は引数の数、``argv``は``char型``で引数を保持。

# 詳細

以下を適当に作ります。今回は``main.cpp``で保存。

```cpp
#include <iostream>
#include <string>

int main(int argc, char* argv[]){
    std::cout << "argc = " << argc << std::endl;
    for(int i=0; i<argc; i++){
        std::cout << "argv["
            << std::to_string(i)
            << "] = "
            << argv[i]
            << std::endl;
    }
    return 0;
}
```

以下でコンパイルして実行します。

```bash
$ g++ -o main main.cpp

$ ./main

argc = 1
argv[0] = ./main
```

引数は指定していないので、``argv``には実行ファイル``./main``自身のみ格納されており期待通りの出力です。

次に引数を指定してみます。

```bash
$ ./main 10 -o ./output

argc = 4
argv[0] = ./main
argv[1] = 10
argv[2] = -o
argv[3] = ./output
```

期待通りですね。
