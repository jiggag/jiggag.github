---
layout: post
published: true
title: ���� �����췯 ������ ���� �˰� �� ��
subtitle: ���� ������
tags: [spring,quartz,scheduler,error]
---

������ ������Ʈ ���� �� ���������췯�� ���ο� ������ ����ϴ� ������ �߻��߰� �̿� �˰Ե� ���� ����α�

```


# ���� 1 :
    
	java.lang.IllegalStateException
		Caused by: org.springframework.beans.factory.BeanCreationException
			Caused by: org.springframework.beans.BeanInstantiationException
				Caused by: org.quartz.ObjectAlreadyExistsException

	- �������� �̸��� �ߺ������� �߻�

# ���� 2 :

	java.lang.IllegalStateException
		Caused by: org.springframework.beans.factory.BeanCreationException
			Caused by: org.springframework.beans.BeanInstantiationException
				Caused by: org.apache.ibatis.binding.BindingException

	- ��Ȯ�� ������ ���� ���ϳ� ��򰡿� ������� ���� bean�� ��û���� �� �߻�

```