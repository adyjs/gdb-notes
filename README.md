# GDB-notes  
how to use gdb tutorial

GDB 是一個常用來了解程式如何運作，以及 debugging 的工具，  
當 C 語言程式運作不合預期 / 在執行時期出現 segmentation fault，  
就可以使用 GDB 來隨著程式一起運作，一步一步找到程式出錯的的行數，  
進而縮小 debug 的範圍


### 開始使用 gdb

有一個 test.c 檔案

```bash
開始使用
$ gdb ./test.c
```

### 設定 breakpoint

設定 breakpoint 有兩種方法
1. 以程式內某一個 function 為中斷點，會開始 step by step 運作
```
$ break main
```

2. 以程式內某一行，會開始 step by step
```
$ break test.c : LINE_NUMBER  
```

### 開始運作

打 run 或 r 指令，告訴 GDB 開始執行 test.c 程式

或者在程式執行到一半時，下 r 指令會重新執行程式


### 下一步

當 GDB 跑到中斷點，會暫停等待指令，  
這時候要下 next 或 n 指令，告訴 GDB 繼續下一步  


### 顯示當前執行的程式碼

當 GDB 一步一步跑得時候，有時候我們會混亂現在程式跑到那一行了，  
這時候只要下 list 或 l 指令，GDB 就會列出當前執行程式碼的前後幾行程式，  
如果在下一次 list 或 l 指令，就會再列出接下來的程式碼，  

看完程式碼，如果要回到當前的程式碼行數，只要下 
```
l LINE_NUMBER
```
就可以了

### 顯示相關變數內容 / 執行時期變數賦值

1. print || p
```
$ print VARIABLE_NAME
```

2. info locals
```
$ info locals
```
可以顯示該 function 內所有的區域變數內容

3. 執行時期變數賦值

```
p VARIABLE_NAME = value
```
可以在執行時期給變數賦值，  
這樣就不用停下 GDB，改程式來測試，  
直接可以在 GDB 執行時期 debug，得知測試結果

### 重複指令

如果上一個指令是 next | n  
那如果當前不下新指令，直接按 enter 時，就會重複上一個指令

### continue | c

讓程式繼續執行到結束