# HDFS

## Task 1
На вход скрипту подается имя файла, на выходе нужно получить имя сервера или IP-адрес, с которого будет читаться первый блок данных (реплик может быть несколько, засчитываться будет любой из них). Пример:

    $ ./run.sh /data/access_logs/big_log/access.log.2015-12-10
    mipt-node01.atp-fivt.org

## Task 2
На вход скрипту подается имя файла, на выходе нужно получить первые 10 байт этого файла (hadoop fs -cat / head, tail и hdfs dfs -cat.. использовать нельзя)

    $ ./run.sh /data/access_logs/big_log/access.log.2015-12-10
    41.190.60.

## Task 3

На вход скрипту подается полный путь до файла в HDFS, на выходе нужно получить размер файла в блоках (см. hdfs fsck -h).

    $ ./run.sh /data/access_logs/big_log/access.log.2015-12-10    
    8


## Task 4
На вход скрипту подается идентификатор блока, на выходе нужно получить имя сервера (если их несколько, то выбрать любой), где хранится данный блок и физический путь в локальной файловой системе до этого блока данных. (О том, как зайти на ноды кластера, написано в материалам cеминара по HDFS)

    $ ./run.sh blk_1075127191
    bds03.vdi.mipt.ru:/dfs/dn/current/BP-76251478-10.55.163.141-1427134131440/current/finalized/subdir21/subdir35/blk_1075127191

## Task 5
Большие файлы на кластере делятся на блоки определенного размера. Нужно выяснить какой дополнительный объем используется в HDFS для хранения данных при использовании одной реплики (т.е. без дублирования данных). Для проведения экспериментов и создания файлов разного размера предлагается использовать утилиту dd (см. пример использования) + решение задачи 4. На вход программы подается размер файла в байтах, на выходе программы должно быть одно число, равное числу байт для физического хранения этого файла (без учета хранения файлов с расширением .meta). Из полученного результата вычесть объём исходного файла (в байтах).

    $ ./run.sh <int>
    123
