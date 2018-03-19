---
layout: post
published: true
title: �ޱַ� ����Ʈ ������Ʈ ����
subtitle: angular-seed-master.git
tags: [angularjs,frontend,project]
---

����Ʈ�� �鿣�尡 ���еǾ� �ִ� ������Ʈ�� ó�� ������ ���� �������� ���� �����غ��� �ͼ��������� �Ѵ�.


������ mvc ������Ʈ�� ����Ʈ�� �鿣�尡 �ϳ��� ������Ʈ���� ������ �͸� ���ϴٰ� ����Ʈ�� angularjs�� �鿣��� java�� ���еǾ� �ִ� ������Ʈ�� ���ϰ� �Ǿ���.
����Ʈ�� npm start, �鿣��� gradlew build �Ǿ� �ִ� jar������ �����Ű�� ������Ʈ..
���� angularjs ������Ʈ�� �����غ���.

## angularjs-seed repository �ٿ�

[angular-seed](http://github.com/angular/angular-seed) repository�� clone�Ͽ� ������Ʈ�� �ٿ�޴´�.
�̴� angular 1, anularjs�� �̿��� ������Ʈ�̴�.

```

$ git clone http://github.com/angular/angular-seed.git	# repository �ٿ�ε�
$ cd angular-seed
$ ren angular-seed jiggag-front-angular	# ������Ʈ ������ ���� : ren [���� ����/���ϸ�] [���� ����/���ϸ�]
$ npm install	# ������Ʈ�� ����� ����� npm�� ���� ��ġ
$ npm start	# http://localhost:8000 

```

#### ���� npm�� �̿��ϱ� ���ؼ��� [nodejs](https://nodejs.org/en/)�� ��ġ�Ǿ� �־���Ѵ�..

�⺻���� ����Ʈ �������� �����Ǿ���.
���� test �ҽ��� �����ϰ� �����ϱ� ���� ���� �������� �����ϰ����Ѵ�.

#### ���� ���Ѱ�..?


## ������Ʈ ���� ����

```

# ������ ������Ʈ ����

app/
	components
	view1
	view2
	app.css
	app.js
	index.html
	index-async.html
e2e-tests/
	protractor.conf.js
	scenarios.js
.bowerrc
.gitignore
.jshintrc
.travis
bower.json
karma.conf.js
license
package.json


# ��� ��ġ ��� ���� : .bowerrc

"directory": "src/vendor"	# "app/bower-components"


# ���� ��� ���� : package.json

"start": "http-server -a localhost -p 8000 -c-1 ./src",


# �׸��� ����.. ����� ���� ������Ʈ ����
src/
	app/
		view1/
			view1.html
		app.js
	assets/
		app.css
	common/
		version/
			...
	vendor/
		angular/
		angular-route/
	index.html
	index-async.html
test/
	app/
		view1/
			view1.test
	common/
		version/
	e2e-tests/
		protractor.conf.js
		scenarios.js
	karma.conf.js
.bowerrc
.gitignore
.jshintrc
.travis
bower.json
license
package.json

```

������ ����θ� ����Ǿ��ٸ� https://localhost:8000/ ȣ�� �� src/index.html �� ȣ�� �� ���̰�
index.html���ο� ����� �������� ���� ���̴�.

#### ����� ��ο� ���� �����׽�Ʈ ������ ���� �ʿ�..


#### [angularjs������Ʈ](https://github.com/jiggag/angularjs-front-base) github
