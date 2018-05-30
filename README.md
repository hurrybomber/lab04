Laboratory work IV
Данная лабораторная работа посвещена изучению систем автоматизации сборки проекта на примере CMake

$ open https://cmake.org/
Tasks
 1. Создать публичный репозиторий с названием lab04 на сервисе GitHub
 2. Ознакомиться со ссылками учебного материала
 3. Выполнить инструкцию учебного материала
 4. Составить отчет и отправить ссылку личным сообщением в Slack
Tutorial
$ export GITHUB_USERNAME=hurrybomber //создаем переменную
$ cd ${GITHUB_USERNAME}/workspace //переходим в каталог
$ pushd . //сохранить каталог и перейти в текущий
~/hurrybomber/workspace ~/hurrybomber/workspace
$ source scripts/activate //выполнить скрипт
$ git clone https://github.com/hurrybomber/lab03.git projects/lab04 //клонировать содержимое
Cloning into 'projects/lab04'...
remote: Counting objects: 15, done.
remote: Compressing objects: 100% (10/10), done.
remote: Total 15 (delta 1), reused 9 (delta 0), pack-reused 0
Unpacking objects: 100% (15/15), done.
$ cd projects/lab04 //переход в каталог
$ git remote remove origin //управление репозиторием
$ git remote add origin https://github.com/hurrybomber/lab04.git //добавить в репозиторий
$ g++ -I./include -std=c++11 -c sources/print.cpp //скомпилировать код
$ ls print.o //вывести содержимое
print.o
$ nm print.o | grep print //информация о символах в файле
0000000000000000 T __Z5printRKNSt3__112basic_stringIcNS_11char_traitsIcEENS_9allocatorIcEEEERNS_13basic_ostreamIcS2_EE
0000000000000210 T __Z5printRKNSt3__112basic_stringIcNS_11char_traitsIcEENS_9allocatorIcEEEERNS_14basic_ofstreamIcS2_EE
$ ar rvs print.a print.o //архиватор
ar: creating archive print.a
a - print.o
$ file print.a //информация о файле
print.a: current ar archive random library
$ g++ -I./include -std=c++11 -c examples/example1.cpp //компиляция
$ ls example1.o //содержимое каталога
example1.o
$ g++ example1.o print.a -o example1 //компиляция
$ ./example1 && echo //выполнить и вывести в терминал
hello
$ g++ -I./include -std=c++11 -c examples/example2.cpp //скомпилировать
$ nm example2.o //информация о символах в файле
000000000000379c s GCC_except_table0
0000000000003870 s GCC_except_table29
00000000000037f0 s GCC_except_table7
0000000000003824 s GCC_except_table8
U __Unwind_Resume
U __Z5printRKNSt3__112basic_stringIcNS_11char_traitsIcEENS_9allocatorIcEEEERNS_14basic_ofstreamIcS2_EE
U __ZNKSt3__16locale9has_facetERNS0_2idE
U __ZNKSt3__16locale9use_facetERNS0_2idE
0000000000003030 T __ZNSt3__111char_traitsIcE11eq_int_typeEii
0000000000003020 T __ZNSt3__111char_traitsIcE11to_int_typeEc
00000000000030d0 T __ZNSt3__111char_traitsIcE12to_char_typeEi
00000000000030a0 T __ZNSt3__111char_traitsIcE2eqEcc
0000000000002ef0 T __ZNSt3__111char_traitsIcE3eofEv
0000000000003780 T __ZNSt3__111char_traitsIcE6lengthEPKc
0000000000003050 T __ZNSt3__111char_traitsIcE7not_eofEi
U __ZNSt3__112basic_stringIcNS_11char_traitsIcEENS_9allocatorIcEEE6__initEPKcm
U __ZNSt3__112basic_stringIcNS_11char_traitsIcEENS_9allocatorIcEEED1Ev
0000000000002f00 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE11__read_modeEv
00000000000030f0 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE12__write_modeEv
0000000000003260 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE4openEPKcj
0000000000001750 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE4syncEv
00000000000006a0 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE5closeEv
0000000000000b00 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE5imbueERKNS_6localeE
0000000000000d40 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE6setbufEPcl
0000000000001030 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE7seekoffExNS_8ios_base7seekdirEj
0000000000001500 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE7seekposENS_4fposI11__mbstate_tEEj
00000000000028b0 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE8overflowEi
0000000000002760 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE9pbackfailEi
0000000000001da0 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEE9underflowEv
0000000000003240 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEEC1Ev
0000000000003530 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEEC2Ev
0000000000000ad0 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEED0Ev
0000000000000580 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEED1Ev
00000000000005a0 T __ZNSt3__113basic_filebufIcNS_11char_traitsIcEEED2Ev
U __ZNSt3__113basic_ostreamIcNS_11char_traitsIcEEED0Ev
U __ZNSt3__113basic_ostreamIcNS_11char_traitsIcEEED1Ev
U __ZNSt3__113basic_ostreamIcNS_11char_traitsIcEEED2Ev
0000000000000520 T __ZNSt3__114basic_ofstreamIcNS_11char_traitsIcEEED0Ev
0000000000000440 T __ZNSt3__114basic_ofstreamIcNS_11char_traitsIcEEED1Ev
0000000000000480 T __ZNSt3__114basic_ofstreamIcNS_11char_traitsIcEEED2Ev
U __ZNSt3__115basic_streambufIcNS_11char_traitsIcEEE5uflowEv
U __ZNSt3__115basic_streambufIcNS_11char_traitsIcEEE6xsgetnEPcl
U __ZNSt3__115basic_streambufIcNS_11char_traitsIcEEE6xsputnEPKcl
U __ZNSt3__115basic_streambufIcNS_11char_traitsIcEEE9showmanycEv
U __ZNSt3__115basic_streambufIcNS_11char_traitsIcEEEC2Ev
U __ZNSt3__115basic_streambufIcNS_11char_traitsIcEEED2Ev
U __ZNSt3__16localeC1ERKS0_
U __ZNSt3__16localeD1Ev
U __ZNSt3__17codecvtIcc11__mbstate_tE2idE
U __ZNSt3__18ios_base4initEPv
U __ZNSt3__18ios_base5clearEj
U __ZNSt3__19basic_iosIcNS_11char_traitsIcEEED2Ev
U __ZNSt8bad_castC1Ev
U __ZNSt8bad_castD1Ev
U __ZSt9terminatev
0000000000003970 D __ZTCNSt3__114basic_ofstreamIcNS_11char_traitsIcEEEE0_NS_13basic_ostreamIcS2_EE
0000000000003a60 D __ZTINSt3__113basic_filebufIcNS_11char_traitsIcEEEE
U __ZTINSt3__113basic_ostreamIcNS_11char_traitsIcEEEE
00000000000039c0 D __ZTINSt3__114basic_ofstreamIcNS_11char_traitsIcEEEE
U __ZTINSt3__115basic_streambufIcNS_11char_traitsIcEEEE
U __ZTISt8bad_cast
0000000000003ab0 S __ZTSNSt3__113basic_filebufIcNS_11char_traitsIcEEEE
0000000000003a80 S __ZTSNSt3__114basic_ofstreamIcNS_11char_traitsIcEEEE
0000000000003950 D __ZTTNSt3__114basic_ofstreamIcNS_11char_traitsIcEEEE
U __ZTVN10__cxxabiv120__si_class_type_infoE
00000000000039d8 D __ZTVNSt3__113basic_filebufIcNS_11char_traitsIcEEEE
0000000000003900 D __ZTVNSt3__114basic_ofstreamIcNS_11char_traitsIcEEEE
U __ZTVNSt3__18ios_baseE
U __ZTVNSt3__19basic_iosIcNS_11char_traitsIcEEEE
U __ZTv0_n24_NSt3__113basic_ostreamIcNS_11char_traitsIcEEED0Ev
U __ZTv0_n24_NSt3__113basic_ostreamIcNS_11char_traitsIcEEED1Ev
0000000000000550 T __ZTv0_n24_NSt3__114basic_ofstreamIcNS_11char_traitsIcEEED0Ev
00000000000004f0 T __ZTv0_n24_NSt3__114basic_ofstreamIcNS_11char_traitsIcEEED1Ev
U __ZdaPv
U __ZdlPv
U __Znam
0000000000000ac0 T ___clang_call_terminate
U ___cxa_allocate_exception
U ___cxa_begin_catch
U ___cxa_end_catch
U ___cxa_throw
U ___gxx_personality_v0
U ___stack_chk_fail
U ___stack_chk_guard
U _fclose
U _fflush
U _fopen
U _fread
U _fseek
U _fseeko
U _ftello
U _fwrite
0000000000000000 T _main
U _memcpy
U _memmove
U _memset
U _strlen

$ g++ example2.o print.a -o example2 //компиляция
$ ./example2 //выполнить
$ cat log.txt && echo //вывод в единный поток
hello
$ rm -rf example1.o example2.o print.o //удаление файлов
$ rm -rf print.a //аналогично
$ rm -rf example1 example2 //аналогично
$ rm -rf log.txt //аналогично
$ cat > CMakeLists.txt <<EOF //записать в файл следующие строки
cmake_minimum_required(VERSION 3.0)
project(print)
EOF
$ cat >> CMakeLists.txt <<EOF //записать в файл следующие строки
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
EOF
$ cat >> CMakeLists.txt <<EOF //записать в файл следующие строки
add_library(print STATIC \${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)
EOF
$ cat >> CMakeLists.txt <<EOF //записать в файл следующие строки
include_directories(\${CMAKE_CURRENT_SOURCE_DIR}/include)
EOF
$ cmake -H. -B_build //подготовка к построению проекта, проверка работоспособности, запись отчета в файл
-- The C compiler identification is AppleClang 9.0.0.9000039
-- The CXX compiler identification is AppleClang 9.0.0.9000039
-- Check for working C compiler: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/cc
-- Check for working C compiler: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/c++
-- Check for working CXX compiler: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /Users/mac/WhiteRabbitRo/workspace/projects/lab04/_build

$ cmake --build _build //создание уже сгенерированного двочиного дерева проекта
Scanning dependencies of target print
[ 50%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[100%] Linking CXX static library libprint.a
[100%] Built target print
$ cat >> CMakeLists.txt <<EOF //записать в файл следующие строки

add_executable(example1 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example1.cpp)
add_executable(example2 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example2.cpp)
EOF
$ cat >> CMakeLists.txt <<EOF //записать в файл следующие строки

target_link_libraries(example1 print)
target_link_libraries(example2 print)
EOF
$ cmake --build _build //конструктор
-- Configuring done
-- Generating done
-- Build files have been written to: /Users/mac/WhiteRabbitRo/workspace/projects/lab04/_build
[ 33%] Built target print
Scanning dependencies of target example2
[ 50%] Building CXX object CMakeFiles/example2.dir/examples/example2.cpp.o
[ 66%] Linking CXX executable example2
[ 66%] Built target example2
Scanning dependencies of target example1
[ 83%] Building CXX object CMakeFiles/example1.dir/examples/example1.cpp.o
[100%] Linking CXX executable example1
[100%] Built target example1

$ cmake --build _build --target print
[100%] Built target print
$ cmake --build _build --target example1
[ 50%] Built target print
[100%] Built target example1
$ cmake --build _build --target example2
[ 50%] Built target print
[100%] Built target example2
$ ls -la _build/libprint.a //информация о каталоге
-rw-r--r--  1 mac  staff  7176 19 мар 12:31 _build/libprint.a
$ _build/example1 && echo
hello
$ _build/example2
$ cat log.txt && echo //вывод в поток
hello
$ rm -rf log.txt //удаление файла
$ git clone https://github.com/tp-labs/lab04 tmp //клонирование файла
Cloning into 'tmp'...
remote: Counting objects: 37, done.
remote: Total 37 (delta 0), reused 0 (delta 0), pack-reused 37
Unpacking objects: 100% (37/37), done.
$ mv -f tmp/CMakeLists.txt . //переименовать
$ rm -rf tmp //удалить
$ cat CMakeLists.txt //вывод содержимого в поток
cmake_minimum_required(VERSION 3.0)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

option(BUILD_EXAMPLES "Build examples" OFF)

project(print)

add_library(print STATIC ${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)

target_include_directories(print PUBLIC
$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
$<INSTALL_INTERFACE:include>
)

if(BUILD_EXAMPLES)
file(GLOB EXAMPLE_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/examples/*.cpp")
foreach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
get_filename_component(EXAMPLE_NAME ${EXAMPLE_SOURCE} NAME_WE)
add_executable(${EXAMPLE_NAME} ${EXAMPLE_SOURCE})
target_link_libraries(${EXAMPLE_NAME} print)
install(TARGETS ${EXAMPLE_NAME}
RUNTIME DESTINATION bin
)
endforeach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
endif()

install(TARGETS print
EXPORT print-config
ARCHIVE DESTINATION lib
LIBRARY DESTINATION lib
)

install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/ DESTINATION include)
install(EXPORT print-config DESTINATION cmake)

$ cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install //конструктор
-- Configuring done
-- Generating done
-- Build files have been written to: /Users/mac/WhiteRabbitRo/workspace/projects/lab04/_build

$ cmake --build _build --target install //конструктор
[100%] Built target print
Install the project...
-- Install configuration: ""
-- Installing: /Users/hurrybomber/workspace/projects/lab04/_install/lib/libprint.a
-- Installing: /Users/hurrybomber/workspace/projects/lab04/_install/include
-- Installing: /Users/hurrybomber/workspace/projects/lab04/_install/include/print.hpp
-- Installing: /Users/hurrybomber/workspace/projects/lab04/_install/cmake/print-config.cmake
-- Installing: /Users/hurrybomber/workspace/projects/lab04/_install/cmake/print-config-noconfig.cmake

$ tree _install //создание дерева
_install
├── cmake
│   ├── print-config-noconfig.cmake
│   └── print-config.cmake
├── include
│   └── print.hpp
└── lib
└── libprint.a

3 directories, 4 files
$ git add CMakeLists.txt //добавить файл
$ git commit -m"added CMakeLists.txt" //создать коммит
[master e44ce18] added CMakeLists.txt
1 file changed, 36 insertions(+)
create mode 100644 CMakeLists.txt

$ git push origin master //загрузить на Git
Username for 'https://github.com': hurrybomber
Password for 'https://hurrybomber@github.com':
Counting objects: 18, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (13/13), done.
Writing objects: 100% (18/18), 2.77 KiB | 1.38 MiB/s, done.
Total 18 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), done.
To https://github.com/hurrybomber/lab04.git
* [new branch]      master -> master
Report
$ popd //возвращение на верхний стэк
~/hurrybomber/workspace
$ export LAB_NUMBER=04 //создание переменной
$ git clone https://github.com/tp-labs/lab04 tasks/lab${LAB_NUMBER} //клонировать с Git'а
Cloning into 'tasks/lab04'...
remote: Counting objects: 37, done.
remote: Total 37 (delta 0), reused 0 (delta 0), pack-reused 37
Unpacking objects: 100% (37/37), done.

$ mkdir reports/lab04 //создаем папку
$ cp tasks/lab04/README.md reports/lab04/REPORT.md //копируем файлы
$ cd reports/lab04 //переходим в каталог
$ edit REPORT.md //открываем отчет
$ gistup -m "lab04" //загружает гит
