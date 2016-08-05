# WikiStat


## 환경

* Python 2.x
* pip


## 준비

    pip install -r requirements.txt

virtualenv 사용을 권장합니다.


## 생성

수집: `logs` 디렉토리에 날짜별 통계 파일이 저장됩니다.

    python -m wikistat.collect

리포트 생성: `index.html`이 생성됩니다.

    python -m wikistat.report

두가지를 주기적으로 실행해주면 됩니다.


## 현재 발생한 문제

root@kiwiwiki:/var/www/wikistat# python -W ignore -m wikistat.collect
librewiki [Errno 1] _ssl.c:510: error:14077438:SSL routines:SSL23_GET_SERVER_HELLO:tlsv1 alert internal error
osawiki [Errno 1] _ssl.c:510: error:14077438:SSL routines:SSL23_GET_SERVER_HELLO:tlsv1 alert internal error
Traceback (most recent call last):
  File "/usr/lib/python2.7/runpy.py", line 162, in _run_module_as_main
    "__main__", fname, loader, pkg_name)
  File "/usr/lib/python2.7/runpy.py", line 72, in _run_code
    exec code in run_globals
  File "/var/www/wikistat/wikistat/collect.py", line 53, in <module>
    main('sites.yml', 'logs')
  File "/var/www/wikistat/wikistat/collect.py", line 31, in main
    assert nchanges >= 1
AssertionError

--대부분의 위키를 지우고 한 결과 CloudFlare SSL을 인식하지 못하는듯함. 어째서?!--
뭐야 이건!! 클플 쓰는곳인건 같은데 보안은 아니야!!
