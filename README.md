# Arduino CPU

Arduino pro micro を３つ使った 4ビット CPU もどきです。

## プログラムの説明

### プログラムカウンター

ボタンを押すとカウントアップします。16になったらカウントアップが終了します。

### フェッチ
  
microSDカードからマシンコードを読み込んでデータバスに流します。
マシンコードは0と1で書かれたテキストファイルです。program.txt で microSD カードに保存します。

### 実行ユニット
  
ADD命令、JMP命令、MOV命令などを実行します。

## 命令セット

| マシンコード | ニーモニック |      |
| ---- | ---- | ---- |
| 0000 | NOP | 何もしない |
| 0001<br>XXXX | JMP XXXX | XXXXへジャンプ |
| 0010<br>XXXX | JNC XXXX | キャリーフラッグが立っていなければXXXXへジャンプ |
| 0011 | RND B | Bレジスタに0〜15のランダムな値を入れる |
| 0100 | MOV A,0 | Aレジスタに0を入れる |
| 0101 | MOV B,0 | Bレジスタに0を入れる |
| 0110 | MOV A,B | AレジスタにBレジスタの値を入れる |
| 0111 | MOV B,A | BレジスタにAレジスタの値を入れる |
| 1000 | ADD A,1 | Aレジスタに1を加える |
| 1001 | ADD A,2 | Aレジスタに2を加える |
| 1010 | ADD A,A | Aレジスタを2倍にする |
| 1011 | ADD A,B | AレジスタにBレジスタの値を加える |
| 1100 | HALT | 終了する |
| 1101 | ---- | |
| 1110 | LD A,XXXX | Aレジスタに RAM[XXXX] の値を入れる |
| 1111 | ST A,XXXX | Aジレスタの値を RAM[XXXX] に入れる |

## サンプルコード

```
0100
1000
0010
0001
0011
0011
0011
0011
0011
0011
0011
0011
0011
0011
1011
0101
```
