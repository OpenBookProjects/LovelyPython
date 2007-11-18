##language:zh
##OBP��Ŀͼ��reSTͨ������ģ��
#format rst
:status: �ݸ�|У��|��ʽ;HuangYi;��ɶ�60%;

.. contents::
  :depth: 3

========
����ʵ��
========

ͨ�����˵����"�������"������ python �������"����"�������������ĺ���̫����
ʵ������������Ҫ���۵�ֻ���û��Զ���������Щ���ʵ�����ѣ��༰��ʵ����ֻ�Ƕ������������е�һԱ��

������
------

::
  
  >>> class Klass(object):
  ...     ' docstring... '
  ...     def __init__(self, a):
  ...         self.attr_a = a
  ...
  >>> Klass.__doc__
  ' docstring... '
  >>> obj = Klass(1)
  >>> obj.attr_a
  1

�ؼ��� ``class`` ����һ���࣬ ``Klass`` ��������֣������� ``object`` �����Ļ��࣬
python �����е� ``class`` ���Ǵ� ``object`` �̳ж���
����Ȼ��Ŀǰ�� python �汾�л�����һ����ν�� old-style class �������ǲ��� ``object`` �̳ж����ģ�������ֻ��Ϊ�˱����������Բ��Һܿ��Ҫ�� python3.0 �г����˳���ʷ��̨��������������ֱ�Ӻ������ˣ���

��������Բ�ͬ���ǣ�python �й��캯������ ``__init__`` ����һ���������ݵľ��ǽ�Ҫ��ʼ����ʵ��������������������е� ``this`` ��

�ͺ���һ����class Ҳ���Զ����ĵ��ַ�����ͬ����ͨ�� ``__doc__`` ���ʡ�

����ʵ�����󲢲���Ҫѧϰ�µ��﷨������ʵ���ͺ�������һ��һ�������� ``Klass`` �Ĳ������մ������캯�� ``__init__`` ��������ֵ�����´�����ʵ������

����
----

�ڹ��캯���е� ``self.attr_a = a`` ��� ``self`` �������������һ����Ϊ ``attr_a`` �����ԣ���󶨵Ķ�����Ǵ���Ĳ��� ``a`` ���󶨵Ķ���

����� ``__dict__`` ���Կ����������ֵ�ķ�ʽ�鿴������������ԣ�::

  >>> obj.__dict__
  {'attr_a': 1}

�����ڹ��캯���У���ʵ���κ�ʱ���㶼���Ը������������ԣ���ֻ��Ҫ�������ڵ����԰󶨶��󼴿ɣ�python ���Զ����������ڵ����ԣ�::

  >>> obj.attr_b = 1
  >>> obj.attr_b
  1
  >>> obj.__dict__
  {'attr_b': 1, 'attr_a': 1}

�������ԣ���Ҫ��ȷ��һ��������ǲ���ʵ�����������ԣ���Ҳ�Ƕ�������ȻҲ�����ԣ�::

  >>> class Klass1(object):
  ...     ' docstrign... '
  ...     class_attr1 = 'hello'
  ...     def __init__(self, a):
  ...         self.attr_a = a
  ...
  >>> Klass1.class_attr1
  'hello'

����Ҳ����ʹ�� ``__dict__`` ���鿴�������������ԣ�

  >>> from pprint import pprint
  >>> pprint(dict(Klass1.__dict__))
  {'__dict__': <attribute '__dict__' of 'Klass1' objects>,
   '__doc__': ' docstrign... ',
   '__init__': <function __init__ at 0x00FBAEF0>,
   '__module__': '__main__',
   '__weakref__': <attribute '__weakref__' of 'Klass1' objects>,
   'class_attr1': 'hello'}

class �����ԱȽ϶࣬Ϊ�˷���鿴����ʹ���� ``pprint`` ģ���е� ``pprint`` �������书�����Ը��ɶ��ķ�ʽ���һЩ�������ݽṹ��
�����÷����Բ鿴 python �Դ��ֲᡣ

������ʵ�����������ʱ��������Բ����ڣ����Զ��������Ӧ�����������ԣ�::

  >>> obj1 = Klass1(1)
  >>> obj1.class_attr1
  'hello'

�������Ǻ����������ԣ�ͬһ������������ʵ��������ͬһ�������ԣ�::

  >>> obj2 = Klass1(2)
  >>> Klass1.class_attr1 = 'changed'
  >>> obj1.class_attr1
  'changed'
  >>> obj2.class_attr1
  'changed'

����
----

::

  >>> class Klass(object):
  ...     def __init__(self, name):
  ...         self.name = name
  ...     def greet_to(self, name):
  ...         print self.name, 'say hello to', name
  ...
  >>> obj = Klass('HuangYi')
  >>> obj.greet_to('you')
  HuangYi say hello to you
  >>> pprint(dict(Klass.__dict__))
  {'__dict__': <attribute '__dict__' of 'Klass' objects>,
   '__doc__': None,
   '__init__': <function __init__ at 0x010122B0>,
   '__module__': '__main__',
   '__weakref__': <attribute '__weakref__' of 'Klass' objects>,
   'greet_to': <function greet_to at 0x010122F0>}

������ʵҲ�����ԣ�׼ȷ��˵�����������������ԡ��� ``Klass`` �����Ƕ��������������� ���캯�� ``__init__`` ����ͨ���� ``greet_to`` ��

����������˵��ʵ�ǶԺ�����һ��򵥰�װ������װ�����þ��ǽ����÷����������������һ����������ȥ��
�����ڶ��巽����ʱ��ǧ�������������һ������������Լ��������������ǽ��� ``self`` ��::

  >>> obj.greet_to
  <bound method Klass.greet_to of <__main__.Klass object at 0x0101C550>>
  >>> Klass.__dict__['greet_to']
  <function greet_to at 0x010122F0>

ֱ��ͨ��ʵ������ ``obj`` �������� ``greet_to`` ʱ�õ�����ʵ�Ƕ����������װ�������"����"��
ֱ��ͨ�� ``Klass.__dict__`` ȡ ``greet_to`` ����ʵ�ʰ󶨵Ķ���ʱ����õ��Ĳ��������û�о�����װ��"����"�ĺ�����

  >>> func = Klass.__dict__['greet_to']
  >>> func(obj, 'you')
  HuangYi say hello to you

�����Ҫ�������װ�Ǻ�ʱ�Լ���β����ģ�����ʵ���漰�� python ����һ����Ը߼��ĸ�� Descriptors��
�������Ȥ���Բ鿴 Raymond д�ľ��ʽ̳̣�http://users.rcn.com/python/download/Descriptor.htm�������齫����������ܡ�

������������ʶ�������뺯������һ���ϵ�������Ѿ�������������ʵ��һЩ����˼�Ĺ����ˣ�����������ʱ������ӷ�����::

  >>> class Klass(object):
  ...     pass
  ...
  >>> obj = Klass()
  >>> def print_id(obj):
  ...     print id(obj)
  ...
  >>> Klass.print_id = print_id # �ȼ��� Klass.__dict__['print_id'] = print_id
  >>> obj.print_id() # �ȼ��� print_id(obj) 
  16892848

��������
--------

��ν�������Ծ�����Щ����ǰ���������»��ߵ����ԡ����������������ᱻ python ���⴦������ʵ��һЩ�ض������õġ�
���Զ������Լ�������ʱǧ��ǵò�Ҫ��������"���"�����ԡ�

������������
============

���캯������ǰ���Ѿ���ʶ���� ``__init__`` ���ǣ��������������� ``__del__`` ��

TODO ������������

����������
==========

TODO

�Զ������Է���
==============

TODO

�̳�
----

С��
-----


��ϰ
-----

.. macro:: [[PageComment2(nosmiley=1, notify=1)]]


.. macro:: -- HuangYi [[[DateTime(2007-06-26T05:39:25Z)]]]

