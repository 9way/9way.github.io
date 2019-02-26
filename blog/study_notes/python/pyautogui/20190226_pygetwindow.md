# 2019/02/26 使用 pyautogui 的出現的 pygetwindow 錯誤的簡單排解

前幾天我在幫朋友弄 pyautogui 的時候發現在某些舊的沒有 i18n 沒有做很好的舊作業系統上，裝 pyautogui 會出現 encoding error。查了一下是底層依存的 pygetwindow 的 setup.py 的 ```open()``` 在就系統上遇到 utf-8 字元會自動用 cp950 去讀，結果就出錯了。

解決方式很簡單，在本地把 pygetwindow 抓下來，然後把出錯的那一行改成 ```open(...,encoding="utf-8")``` 。在本地先跑過一次 setup.py 裝好 pygetwindow（有可能要先跑 ```chcp 65001``` 先把 shell 改成 utf-8 ）。

之後再用 ```pip3 install pyautogui -e local/path/to/pygetwindow``` 就可以了。

是說，在 windows 上新的 python 的 pillow 造成的 pyqutogui 找不到圖就直接把 script 停掉的問題還是存在啊…
