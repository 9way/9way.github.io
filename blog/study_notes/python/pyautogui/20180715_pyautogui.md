# 2018/07/15 使用 Pyautogui 製作簡單的腳本

## 前置作業

我在 windows 上使用 python 3.4 ，並且使用 ``pip install pyautogui`` 安裝 pyautogui。使用更新版本的 python （像是 3.7）理論上不該有問題，但是在使用圖片搜尋找不到的時候會出現錯誤，因為圖片比對不是我的專門領域，所以我最後回到比較穩定的 3.4 版本。

## 自動按滑鼠

### 取得滑鼠座標
要自動點按滑鼠，會需要知道當時滑鼠在哪個座標上。 pyautogui.position() 可以提供滑鼠座標的數值。

下面這是一個小程式可以在 console 端取得滑鼠座標：
```python
import pyautogui

pyautogui.PAUSE = 2
pyautogui.FAILSAFE = True

print("Press Ctrl-C to quit.")

try:
    while True:
        x, y = pyautogui.position()
        posStr = 'x: ' + str(x).rjust(4) + ' y: ' + str(y).rjust(4)
        print(posStr, end='')
        print('\b'*len(posStr), end='')

        
except KeyboardInterrupt:
    print("Done\n")
```

### 點擊特定座標

假設我們要每隔十秒點擊 (400, 400) 這個座標：

```python
import pyautogui
import time

print("Press Ctrl-C to quit.")

try:
    while True:
		pyautogui.click(400, 400)
		time.sleep(10)

except KeyboardInterrupt:
    print("Done\n")

```
