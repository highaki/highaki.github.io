===================================
reST(reStructuredText)記法のまとめ
===================================


参考ページ
==========

- http://planset-study-sphinx.readthedocs.io/ja/latest/04.html
- http://www.ne.jp/asahi/hishidama/home/tech/sphinx/rest.html


はじめに
=========

Sphinx version: 1.5.6


凡例
=====

::

	<コード>

<表示>


ページ内の目次
===============

.. sourcecode:: none

	.. contents:: これは目次です
		:depth: 2

.. contents:: これは目次です
	:depth: 2


改行
=====

::

	文章途中の改行は
	認識されません。
	
	| 行頭に"| "を付けることでその文章終りで改行します。
	| 改行
	| します。

文章途中の改行は
認識されません。

| 行頭に"| "を付けることでその文章終りで改行します。
| 改行
| してます。


インデント
===========

::

	タブでインデントを下げると字下げできます。
		これは字下げされている文章です。

	これは字下げされていない文章です。

タブでインデントを下げると字下げできます。
	これは字下げされている文章です。

これは字下げされていない文章です。


整形済みテキスト
=================

::

	::
	
		"::"の下に1行空けて、インデントを付けて文章を書くと
		基本的な整形済みテキストです。


	タイトル::
	
		"::"の前に表題を書くと、「タイトル:」の様に出力される。


	.. sourcecode:: python

		# "::" の前に ".. sourcecode" を
		# "::" の後に プログラム言語 を書くことで
		# プログラム言語特有の表示になる。
		import os
		print(os.path)
	
	
	.. sourcecode:: python
		:linenos:
		
		# ":linenos:"を付けると
		# 行数が表示されるようになる
		import os
		print(os.path)

::

	"::"の下に1行空けて、インデントを付けて文章を書くと
	基本的な整形済みテキストです。


タイトル::

	"::"の前に表題を書くと、「タイトル:」の様に出力されます。


.. sourcecode:: python
	
	# "::" の前に ".. sourcecode" を
	# "::" の後に プログラム言語 を書くことで
	# プログラム言語特有の表示になります。
	import os
	print(os.path)


.. sourcecode:: python
	:linenos:
	
	# ":linenos:"を付けると
	# 行数が表示されるようになります
	import os
	print(os.path)


見出し
=======

::

        ========
        見出し1
        ========

        見出し2
        ========

        見出し3
        --------

        見出し4
        ^^^^^^^^

        見出し5
        ~~~~~~~~

        見出し6
        """"""""

※ 見出し1, 見出し2はサンプルなし。

.. _midashi3label:

見出し3
--------

見出し4
^^^^^^^^

見出し5
~~~~~~~~

見出し6
""""""""

リスト
=======

マイナス "``-``" は アスタリスク "``*``" や プラス "``+``" でも可能
::

	- リスト1
		- ネスト リスト1_1
			- ネスト リスト1_1_1
			- ネスト リスト1_1_2
		- ネスト リスト1_2
	- リスト2
	- リスト3

- リスト1
	- ネスト リスト1_1
		- ネスト リスト1_1_1
		- ネスト リスト1_1_2
	- ネスト リスト1_2
- リスト2
- リスト3


番号付きリスト(手動)
=====================

閉じ括弧 "``)``" は ピリオド "``.``" でも可能

::

	1) 番号付きリスト1
		a) 番号付きリスト1_1
		b) 番号付きリスト1_2
	2) 番号付きリスト2
	3) 番号付きリスト3

1) 番号付きリスト1
	a) 番号付きリスト1_1
	b) 番号付きリスト1_2
2) 番号付きリスト2
3) 番号付きリスト3


番号付きリスト(自動)
=====================

.. sourcecode:: none

	#) 番号付きリスト1
		#) 番号付きリスト1_1
		#) 番号付きリスト1_2
	#) 番号付きリスト2
	#) 番号付きリスト3

#) 番号付きリスト1
	#) 番号付きリスト1_1
	#) 番号付きリスト1_2
#) 番号付きリスト2
#) 番号付きリスト3

強調
======

::

	これは *強調レベル1* （斜字）です。
	これは **強調レベル2** （太字）です。

| これは *強調レベル1* （斜字）です。
| これは **強調レベル2** （太字）です。


ラベルと参照
=============

| 見出しの前に "``.. _<任意のラベル名>:``" をつけることで、
| 見出しにラベルを付与することができます。
| ラベルを参照することで、ページ内のどこからでもラベルの場所に移動することができます。
| 参照名は明示的に指定しない場合、
| 参照先の見出し名が自動的に記載されます。
| ラベルを付与できる見出しは :ref:`midashi3label` までです。

.. sourcecode:: none

	.. _mylabel:
	
	サンプル見出し
	---------------

	:ref:`参照のテスト<mylabel>` へ移動
	:ref:`mylabel` へ移動

.. _mylabel:

サンプル見出し
---------------

:ref:`参照のテスト<mylabel>` へ移動
:ref:`mylabel` へ移動


他のドキュメントを参照
=======================

| "``:doc:``" の後にローカルパスからの <ファイルのパス> を記載すると、
| 当該ファイルへ参照できるリンクを作成できます。
| リンク名は明示的に指定しない場合、
| 移動先ファイルの見出しが自動的に記載されます。

.. sourcecode:: none

	:doc:`ほげほげ<./sample/sample>`
	:doc:`./sample/sample`

:doc:`ほげほげ<./sample/sample>`
:doc:`./sample/sample`


リンク
=======

.. sourcecode:: none

	| URLはそのまま記載することで自動的にリンクされます。
	| https://www.google.co.jp/
	| リンク名を記載することも可能です。
	| `googleのトップページです。 <https://www.google.co.jp/>`_
	| ラベルに予めURLを設定しておくことで
	| リンクを簡単に書けます。
	.. _`google homepage`: http://www.google.co.jp/
	| `google homepage`_
	

| URLはそのまま記載することで自動的にリンクされます。
| https://www.google.co.jp/
| リンク名を記載することも可能です。
| `googleのトップページです。 <https://www.google.co.jp/>`_
| ラベルに予めURLを設定しておくことで
| リンクを簡単に書けます。

.. _`google homepage`: http://www.google.co.jp/

| `google homepage`_


ダウンロード用のリンク
=======================

.. sourcecode:: none

	| :download:`このファイルをダウンロード <./tutorial_reST.rst>`
	| :download:`./tutorial_reST.rst`
	
| :download:`このファイルをダウンロード <./tutorial_reST.rst>`
| :download:`./tutorial_reST.rst`


画像の表示
===========

scale
	画像の縮尺
width
	横幅
height
	縦幅
align
	配置指定”top”, “middle”, “bottom”, “left”, “center”, “right”が使えます
alt
	altテキスト

.. sourcecode:: none

	.. image:: /image/sample.jpg
		:scale: 40%
		:align: left
		:alt: sample1
	
	.. image:: /image/sample.jpg
		:height: 300px
		:width: 100px
		:align: center
		:alt: sample2
		
.. image:: /image/sample.jpg
	:scale: 10%
	:align: left
	:alt: sample1

.. image:: /image/sample.jpg
	:height: 300px
	:width: 100px
	:align: center
	:alt: sample2


テーブル1
==========

.. sourcecode:: none

	======= ====== ======
	col1    col2   col3
	======= ====== ======
	row1    a      b
	row2    a      b
	row3    a      b
	======= ====== ======

======= ====== ======
col1    col2   col3
======= ====== ======
row1    a      b
row2    a      b
row3    a      b
======= ====== ======


テーブル2
==========

.. sourcecode:: none

	+------------+------------+-----------+ 
	| Header 1   | Header 2   | Header 3  | 
	+============+============+===========+ 
	| body row 1 | column 2   | column 3  | 
	+------------+------------+-----------+ 
	| body row 2 | Cells may span columns.| 
	+------------+------------+-----------+ 
	| body row 3 | Cells may  | - Cells   | 
	+------------+ span rows. | - contain | 
	| body row 4 |            | - blocks. | 
	+------------+------------+-----------+

+------------+------------+-----------+ 
| Header 1   | Header 2   | Header 3  | 
+============+============+===========+ 
| body row 1 | column 2   | column 3  | 
+------------+------------+-----------+ 
| body row 2 | Cells may span columns.| 
+------------+------------+-----------+ 
| body row 3 | Cells may  | - Cells   | 
+------------+ span rows. | - contain | 
| body row 4 |            | - blocks. | 
+------------+------------+-----------+


csvテーブル
============

.. sourcecode:: none

	.. csv-table:: Frozen Delights!
	    :header: "Treat", "Quantity", "Description"
	    :widths: 15, 10, 30
	
	    "Albatross", 2.99, "On a stick!"
	    "Crunchy Frog", 1.49, "If we took the bones out, it wouldn't be
	    crunchy, now would it?"
	    "Gannet Ripple", 1.99, "On a stick!"

.. csv-table:: Frozen Delights!
    :header: "Treat", "Quantity", "Description"
    :widths: 15, 10, 30

    "Albatross", 2.99, "On a stick!"
    "Crunchy Frog", 1.49, "If we took the bones out, it wouldn't be
    crunchy, now would it?"
    "Gannet Ripple", 1.99, "On a stick!"


注釈
=====

.. sourcecode:: none

	.. note::
	
		これは注釈です！
	
	.. warning::
	
		これは警告です！

.. note::

	これは注釈です！

.. warning::

	これは警告です！


折りたたみ
===========

"折りたたみ"はsphinxの拡張機能で実現できます。

準備として、
`このgithub <https://github.com/scopatz/hiddencode>`_ から
``hidden_code_block.py`` を自身のsphinx( ``conf.py`` と同ディレクトリ)に配置します。  

``conf.py`` の ``extensions`` パラメータに ``hidden_code_block`` を追記します。

そして同じく ``conf.py`` の ``sys.path.insert(0, os.path.abspath('.'))`` のコメントアウトを外します。


詳細は、 https://github.com/scopatz/hiddencode/blob/master/index.rst のInstallationを見ましょう。

.. sourcecode:: none

	.. hidden-code-block:: none
		:starthidden: True
	
		初めは折りたたみ状態のコードブロックです。
	
	.. hidden-code-block:: none
		:starthidden: False
		:linenos:
		:label: hidden-code-sample
	
		初めから見えている状態のコードブロックです。
		ライン番号あり、かつ"hidden-code-sample"のラベル名を付与しています。

.. hidden-code-block:: none
	:starthidden: True

	初めは折りたたみ状態のコードブロックです。

.. hidden-code-block:: none
	:starthidden: False
	:linenos:
	:label: hidden-code-sample

	初めから見えている状態のコードブロックです。
	ライン番号あり、かつ"hidden-code-sample"のラベル名を付与しています。
