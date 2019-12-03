# LeapMotion_ROS
### ★ROSの場合  
* UbuntuにLeapMotionのセットアップを終わらせておく。~~自分で調べろ~~  
#### UbuntuでLeapMotionを使えるようにする
1.  [ココ](https://www.leapmotion.com/developers)でデベロッパーとして登録する。メールとパスワード入力するだけ。  
2. [ココ](https://developer.leapmotion.com/sdk/v2/)からSDKをダウンロードしてくる。  
3. ファイルを解凍してインストール  
`$cd ~/Download`  
`$tar -xzvf Leap_Motion_SDK_Linux_2.3.1.tgz`  
debian用パッケージがあるからそれを使ってインストールする  
`$sudo dpkg --install Leap-1.2.0-x86.deb`
4. LeapSDKディレクトリをホームにコピーする  
`$cp LeapSDK $HOME/`  
5. Pythonがライブラリを見つけられるように環境変数PYTHONPATHを設定してやる  
`export PYTHONPATH=$PYTHONPATH:$HOME/LeapSDK/lib/x86:$HOME/LeapSDK/lib`  

#### ROSで使えるようにする  
* パッケージのインストール  
`$sudo apt-get install ros-kinetic-leap-motion`  
* LeapMotion daemon起動  
`$leapd`  
* LeapMotionとROSノードの起動  
`$roscore`  
`$rosrun leap_motion sender.py`  

### ★Pythonで普通に動かす場合  
* /LeapSDK/lib/x86に入ってる以下の3つのファイルが必要  
    * Leap.py
    * ibLeap.so  
    * LeapPython.so  
* 作業ディレクトリにこれらが無いとLeapMotionからデータ取ってきてくれないから気をつけること  

### 参考になったサイト
* [Leap Motion を Pythonから使う方法を調べた](https://futurismo.biz/archives/6658)
* [Leap Motion + Ubuntu16.04 + Unity(ゲームエンジン)](http://kconcon3.hatenablog.com/entry/2018/02/08/230000)  
* [LeapMotionSDK for Python(公式)](https://developer-archive.leapmotion.com/documentation/v2/python/devguide/Leap_Hand.html)  

