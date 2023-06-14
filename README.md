# 無人機飛行載具之智慧計數競賽

以下為重現實驗教學

## 下載程式碼
```
git clone https://github.com/CodeBaron7/TEAM_2096_UAV.git
```

## 資料準備

1. 至官方Download Dataset下載Private Testing Dataset_v2.zip
2. 下載已訓練完成的模型 :  https://drive.google.com/file/d/1f-1MSgxfKgrN9BQGxJgPUEzUfWxECf1m/view?usp=share_link
3. 下載調整後的訓練資料集 : https://drive.google.com/file/d/1iI7mH99AW1orHp4BdhMFrOi6MKpSfuiy/view?usp=share_link
      
      訓練資料調整內容
      1. img0040.png 與 img0040.txt刪除，
      2. img0201 ~ img0400 當作驗證集

下載並解壓好後將資料夾 "dataset" 與 "Private Testing Dataset_v2" 以及訓練好後的模型 "v18.pt"，放至TEAM_2096_UAV\code目錄下，
請注意檔名需一致。

## 環境配置:

   以下2種方式可2擇1選用:

### 1.於Local端執行
   下方有環境建置教學
   
   作業系統 : Win10 or Linux
   
   Python : 3.9.9         (建議至少3.8以上)
   
   Pytorch : 1.11.0+cu113 (根據CUDA Version選擇)
   
   ***訓練時GPU Memory至少需24GB
   
   CUDA Version: 11.5

### Local端虛擬環境建置教學
   建立虛擬環境並進入
```
Python -m venv yolov7_venv
cd yolov7_venv\Scripts
activate
```
   更新pip與setuptools
```sh
python -m pip install --upgrade pip
pip install --upgrade setuptools
```
   至requirements.txt目錄下安裝其餘函式庫
```sh
pip install -r requirements.txt
```
   依cuda版本安裝對應pytorch函式庫
```sh
pip3 install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu113
```

### 2.執行於TWCC CCS cm.super
      
   容器映像檔pytorch-22.05-py3
  
   至requirements.txt目錄下安裝其餘函式庫
```sh
pip install -r requirements.txt
```

## Train
   至TEAM_2096_UAV\code路徑下輸入  
```sh
python train_aux.py --adam
```
   訓練後模型存放於runs\train\v18\weights

## Inference
   至TEAM_2096_UAV\code路徑下執行
```sh
python detect.py --save-txt
```
Inference後產生的submission.csv提交檔存放於TEAM_2096_UAV\code目錄下


# UAV
