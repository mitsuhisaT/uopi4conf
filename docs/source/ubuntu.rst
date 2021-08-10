.. how to install ubuntu for Raspberry Pi 4B and Pi400.

#################################################################
Ubuntu デスクトップを Raspberry Pi 4B 、 Pi400 にインストールする
#################################################################


***********
事前準備
***********

- `Raspberry Pi 4B`_ の 4GB または 8GB モデル あるいは `Raspberry Pi 400`_
- `Raspberry Pi 4B`_ 対応のケース
- USB 電源アダプター 5V/3A USB Type C
- 16GB 以上の microSD カード
- HDMI 接続可能なモニタまたは TV と HDMIケーブル
- USB 接続のキーボード(Pi400は不要)とマウス

.. warning::

  `Raspberry Pi 4B`_ と `Raspberry Pi 400`_ の HDMI 接続端子は mini HDMI です。100円ショップなどの変換アダプタを使って接続しても良いです。
  `Raspberry Pi 400`_ は、2021年7月13日に技術基準適合証明(技適)の工事設計認証が完了し、7月29日から `日本語キーボード版`_ が発売されています。
  `技術基準適合証明(技適)番号020-210106`_ の形式又は名称は「Raspberry Pi 400」となっているので、英語配列キーボード版も発売されると良いなぁ(切望)。

.. note::

  Raspberry Pi にはオンオフSW が付いていません。SW付きの `Raspberry Pi 4B`_ 対応の電源アダプターを用意しました。

.. note::

  - 日本向け製品では無い 64GB の microSD カードを利用しています。説明文に日本語が無いだけで、同等のモノがとても安く入手できます。

  - 持ち運び用に MISEDI 13.3インチ 4K(UHD) を準備しました。モニター自体の性能は申し分無いのですが、標準設定だと、相対的に文字が小さく、読むの厳しいかな。家で 32インチ 4K に接続している場合は、全く問題ないです。
  - マウスは `logicool M187`_ のブライトレッドを接続しています。公式ケースの赤と相性が良いです。ワイヤレス接続ですが、ドライバーなど必要無く、付属のレシーバーをUSBポートに差し込めばすぐに使えます。

.. note::

  有線LAN接続する場合は、LANケーブル(Gigabit Ethernet を使う場合は Category 6 以上)

.. warning::

  `Raspberry Pi 3B+`_ と Ubuntu Mate と Bluetooth マウスの組み合わせは、起動したけど使いもにならず、でした。


********************************
Ubuntu desktop for Pi4 の準備
********************************

`Ubuntu Desktop Raspberry Pi`_ から Raspberry Pi 用 Desktop (64-bit) のインストールイメージをダウンロードします。

.. note::

  Raspberry Pi 4 Model B の 4GB または 8GB モデル、Pi400 または CM4 (Compute Module 4) で稼働できます。

ダウンロードしたファイル(ISOイメージ)は `balenaEtcher`_ を利用して microSD に *Flash* します。

.. note::

  macOS では Homebrew を利用して ``brew install balenaetcher`` でインストールできます。


**********
初回起動
**********

1. microSD の挿入

  (a) 前のステップで用意した microSD を Raspberry Pi に挿入する

2. ケーブル接続

  (a) HDMI ケーブルを Raspberry Pi (micro HDMI)とモニターに接続する
  (b) USB キーボードとマウスを Raspberry Pi に接続する
  (c) 電源アダプターを Raspberry Pi (Type-C) に接続する
  (d) 有線LAN接続する場合は、LANケーブルを接続する

3. ケーブル接続を確認

4. 電源アダプターをコンセントに挿す

5. セットアッププログラムが起動する

  (a) ログインユーザの設定
  (b) 言語設定： 英語を選択
  (c) Wi-Fi ネットワークの設定
  (d) タイムゾーンの設定

6. 待つ
  (a) ログインプロンプトが表示されるまで待つ
  (b) 5. a. で設定したパスワードを入力すると Ubuntu デスクトップが表示されます


********************
更新とアップグレード
********************

`Show Applications` (左下の9点のアイコン) の2ページの `Utilities` の２ページの `Terminal` をクリックし起動します。

まず、パッケージリストを次のコマンドを入力し更新します。キーボードで `sudo apt update` と入力し、最後に [Enterキー] を入力します。

.. code:: shell

  sudo apt update

リストの更新が完了し、プロンプトが表示されたら、アップグレードをおこないます。

.. code:: shell

  sudo apt upgrade

アップグレードされるアプリケーションやライブラリなどのリストとダウンロードの合計サイズが表示され、

.. code:: shell

  Do you want to continue? [Y/n]

と表示されるので、`y` を入力します。更新されたパッケージをダウンロードし、その後にアップグレードが行われます。

.. warning::

  インストール直後のアップグレードなので、リスタートします。
  右上の電源ボタンをクリックし `Power Off/Logout` から `Restart...` を選択します。


.. note::

  更新とアップグレードは、頻繁に実施することをお勧めします。不具合解消とセキュリティアップデートが実施できます。


.. _logicool M187: https://www.logicool.co.jp/ja-jp/products/mice/m187-mini-wireless-mouse.910-005377.html
.. _balenaEtcher: https://www.balena.io/etcher/
.. _Raspberry Pi 3B+: hhttps://www.raspberrypi.org/products/raspberry-pi-3-model-b-plus/
.. _Raspberry Pi 4B: https://www.raspberrypi.org/products/raspberry-pi-4-model-b/
.. _Raspberry Pi 400: https://www.raspberrypi.org/products/raspberry-pi-400-unit/
.. _Raspberry Pi CM4: https://www.raspberrypi.org/products/compute-module-4/?variant=raspberry-pi-cm4001000
.. _Ubuntu Desktop Raspberry Pi: https://ubuntu.com/download/raspberry-pi
.. _技術基準適合証明(技適)番号020-210106: https://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=020&TC=N&PK=1&FN=210802N020&SN=%94%46%8F%D8&LN=36&R1=*****&R2=*****
.. _Raspberry Pi 400 技適19-3: https://www.tele.soumu.go.jp/giteki/SearchServlet?pageID=jg01_01&PC=020&TC=N&PK=1&FN=210802N020&SN=%94%46%8F%D8&LN=36&R1=*****&R2=*****
.. _日本語キーボード版: https://raspberry-pi.ksyic.com/news/page/nwp.id/102/