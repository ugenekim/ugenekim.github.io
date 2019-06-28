---
layout: post
title: "Redmine Plugin 관리"
date: 2019-06-28 19:51:02
categories: [redmine]
tags: [redmine, plugin]
---

## Plugin 설치
1. ${REDMINE_ROOT}/plugins 디렉토리에 Plugin 복사
```bash
$ cd ${REDMINE_ROOT}/plugins
$ git clone git://github.com/user_name/plugin_name.git
```
or
```bash
$ cp plugin_name.zip ${REDMINE_ROOT}/plugins
$ cd ${REDMINE_ROOT}/plugins
$ unzip plugin_name.zip
```

2. 필요 Ruby package 설치(필요할 경우에만)
    - ${REDMINE_ROOT} 에서 작업  
```bash
$ bundle install
```

3. Redmine 데이터베이스 업데이트(필요할 경우에만)
    - 해당 작업을 하기 전에 디비백업을 받을 것!
    - ${REDMINE_ROOT} 에서 작업   
```bash
$ bundle exec rake redmine:plugins:migrate NAME=plugin_name RAILS_ENV=production
```

4. Redmine 재시작
    - 설치된 Plugin은 'Administration -> Plugins' 에서 확인 가능

## Plugin 삭제
1. Redmine 데이터베이스 업데이트(Downgrade)
```bash
$ bundle exec rake redmine:plugins:migrate NAME=plugin_name VERSION=0 RAILS_ENV=production
```

2. ${REDMINE_ROOT}/plugins 디렉토리에 있는 Plugin 폴더 삭제  
```bash
$ rm -rf ${REDMINE_ROOT}/plugins/plugin_name
```

3. Redmine 재시작
