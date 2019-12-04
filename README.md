# LeapMotion_ROS
### ★ROSの場合  
UbuntuにLeapMotionのセットアップを終わらせておく。
[ここ](https://github.com/ros-drivers/leap_motion)に全部書いてあるよ
#### UbuntuでLeapMotionを使えるようにする
1.  [ココ](https://www.leapmotion.com/developers)でデベロッパーとして登録する。メールとパスワード入力するだけ。  
2. [ココ](https://developer.leapmotion.com/sdk/v2/)からSDKをダウンロードしてくる。  
3. ファイルを解凍してインストール  
`$tar -xzvf Leap_Motion_SDK_Linux_2.3.1.tgz`  
debian用パッケージがあるからそれを使ってインストールする  
`$sudo dpkg --install Leap-2.3.1+31549-x64.deb`
4. LeapSDKディレクトリをホームにコピーする  
`$cp LeapSDK $HOME/`  
5. Pythonがライブラリを見つけられるように環境変数PYTHONPATHを設定してやる  
`$export PYTHONPATH=$PYTHONPATH:$HOME/LeapSDK/lib/x64:$HOME/LeapSDK/lib`  

#### ROSで使えるようにする  
* ROSパッケージのインストール  
`$sudo apt-get install ros-kinetic-leap-motion`  
* LeapMotionのdaemon起動。  
__sudo__ しないと後々パーミッションエラー出まくるから注意  
`$sudo leapd`  
(本家ではサービスリスタートしてる)  
`$sudo service leapd restart`
* LeapMotionの起動  
`$LeapControlPanel`  
* LeapMotionとROSノードの起動  
`$roscore`  
`$rosrun leap_motion sender.py`  

### ★Pythonで普通に動かす場合  
* /LeapSDK/lib/x64に入ってる以下の3つのファイルが必要  
    * Leap.py
    * ibLeap.so  
    * LeapPython.so  
* 作業ディレクトリにこれらが無いとLeapMotionからデータ取ってきてくれないから気をつけること  

### 参考になったサイト
* [Leap Motion を Pythonから使う方法を調べた](https://futurismo.biz/archives/6658)
* [Leap Motion + Ubuntu16.04 + Unity(ゲームエンジン)](http://kconcon3.hatenablog.com/entry/2018/02/08/230000)  
* [LeapMotionSDK for Python(公式)](https://developer-archive.leapmotion.com/documentation/v2/python/devguide/Leap_Hand.html)  

