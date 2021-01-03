# Статическая сборка QT 5.15.2 MinGWx64

Для начала нужно поставить именно Online установку для дополнительных инструментов.

[Скачать онлайн установщик](http://download.qt.io/official_releases/online_installers/qt-unified-windows-x86-online.exe "Скачать онлайн установщик")


Дальше нужно установить:
1. [Python последней версии 64 битную](https://www.python.org/ftp/python/3.8.3/python-3.8.3-amd64.exe "Python последней версии 64 битную")
2. [Perl последней версии 64 битную](http://strawberryperl.com/download/5.30.2.1/strawberry-perl-5.30.2.1-64bit.msi "Perl последней версии 64 битную")
3. [Ruby последней версии 64 битную](https://github.com/oneclick/rubyinstaller2/releases/download/RubyInstaller-2.7.1-1/rubyinstaller-2.7.1-1-x64.exe "Ruby последней версии 64 битную")

чтоб не возникало ошибок cannot find -ltiff нужно скачать с сайта http://www.libtiff.org/ Windows библиотеку TIFF бинарный и указать путь PATH и в configure добавляем пораметр -qt-tiff

[Далее скачиваем исходник QT](http://download.qt.io/official_releases/qt/5.15/5.15.0/single/qt-everywhere-src-5.15.0.zip "Далее скачиваем исходник QT")

Распаковываем его

Переходим него и начинаем

`configure -static -debug-and-release -platform win32-g++ -qt-zlib -qt-pcre -qt-libpng -qt-tiff -qt-libjpeg -qt-freetype -opengl desktop -no-angle -sql-sqlite -openssl -I d:\Qt\Tools\OpenSSL\Win_x64\include -L d:\Qt\Tools\OpenSSL\Win_x64\lib  -opensource -confirm-license -make libs -make tools -nomake examples -nomake tests -prefix c:\Qt\5.15.2\mingw81_64_static`

`mingw32-make -k -j4`

`mingw32-make -k install`

И чтоб отлучить об зависимостей MinGW в проект добавляем

`QMAKE_LFLAGS_RELEASE += -static -static-libgcc`
