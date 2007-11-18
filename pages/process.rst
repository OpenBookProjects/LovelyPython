##language:zh
#format rst

.. contents::

:status: �ݸ� ;HuangYi; 100%;

===================
���̿���
===================

python �������м������ԭ�����﷨����������ֵ���Ϊ���ԣ�
���б�̾�������Ѷ�������Щ�﷨Ӧ������İ����

������������˵������ֻ��Ҫע�����㣬���µ����ݾͿ��Էɿ�������ȥ�ˣ�
һ�� python �������������÷�Χ������������ð�ſ�ͷ��
����������Щ���̿�����䶼���Ը��� ``else`` �Ӿ䣡
``if`` ������� ``else`` �Բ���˵���� ``for`` �� ``while`` ���Ҳ���Ը� ``else`` �Ӿ䣡
������ͬ ``else`` �Ӿ�ĺ�����Ȼ����������Ļ�����ͬ��������ͬ��

if ��֧
=========

��������÷���
::
    
  if a == b:
      print 'a ���� b'
  else:
      print 'a ������ b'

Ҳ���㻹��Ҫ��ϸ�µؿ��ƣ�
::
    
  if a == b:
      print 'a ���� b'
  elif a < b:
      print 'a С�� b'
  elif a > b:
      print 'a ���� b'
  else:
      print '�ڱ����������ǲ����ܵΣ�'

``elif`` ���� ``else if`` ����д��

.. topic:: û�� switch

  python û�� ``switch`` ��䣬���� ``if elif else`` ����Ѿ�����Ӧ���󲿷������
  �����������һ�� ``switch`` Ӧ�ó�����python ���и������ŵķ�ʽ�������뿴��
  ::

    # α�� ��������Ĳ�ͬ����ѡ�����Ĳ�ͬ��Ϊ
    switch( sys.argv[1] ):
        case '-e':
            walk_cd()
        case '-d':
            search_cd()
        ...
        default:
            raise CommandException("Unknown Commend: " + sys.argv[1])

    # ʹ�� if ���
    if sys.argv[1]=='-e':
        walk_cd()
    elif sys.argv[1]=='-d':
        search_cd()
    ...
    else:
        raise CommandException("Unknown Command: " + sys.argv[1])

    # ���õ�����
    commands = {
        '-e'   : walk_cd,
        '-d'   : search_cd,
    }
    try:
        commands[ sys.argv[1] ]()
    except KeyError:
        raise CommandException("Unknown Command: " + sys.argv[1])

  ���һ�ַ�ʽ���ܴӿɶ��ԣ�������Ȼ�ģ������ܣ���ϣ�� vs ��ͨ���ң��϶��߳��ܶࡣ
  �������һ����������������Ϊ��ӳ����ȫ���������ˣ�һ���޸��������䷽�㣬
  ��ʱ��Ҳ�����׽����Ƿ��뵽�����ļ���ȥ��

.. topic:: ��Ԫ�����

  ���ǵ���һ�� python �������͵�ϰ�� 1 ������Ҫ������ and �� or ������ģ�� c ���Ե� ? : ��Ԫ��������
  ʵ������ python2.5 ��ǰ����ȷʵ��һ������ʵ�õļ��ɣ����� python2.5 ��Ӧ��� fans ��ǿ��Ҫ��
  ���ڼ������µ��﷨���Ӵ˿����ø������ķ�ʽ������ֳ��÷�֧��
  ::
    
    >>> def get_length(s):
    ...     # �ȼ���:
    ...     # if(s!=None)
    ...     #     return len(s)
    ...     # else:
    ...     #     return len('None')
    ...     return len(s) if s!=None else len('None')
    ...
    >>> get_length(None)
    4

  �� and or ���ɿ���д�ɣ�
  ::

    >>> def get_length(s):
    ...     return s!=None and len(s) or len('None')
    ...
    >>> get_length(None)
    4

  ������Ȼ�ǵ�һ��д��������˳��һЩ�������� ;-)

for ѭ��
=========
::

  for item in [1, 2, 3]:
      print item

����Ĵ�����ʵ���Ǳ��� ``some_list`` �б�������ÿһ��Ԫ�ض���ӡ������

���Ե�ѭ����䣨��ʵҲ��������� ``for`` �ͺ���� ``while`` �ˣ��ж�����ʹ����ô������䣺
``break`` �� ``continue`` �� ``break`` ��ʾҪ�˳�ѭ���� ``continue`` ��˵ֱ�ӽ��뵽��һ��
��ѭ����ȥ�ɣ�
::

  >>> for item in range(10):
  ...     if item<5:         # ������ 5 С��
  ...         continue       # ������һ��ѭ��
  ...     else:              # �����������Ǵ��ڵ��� 5 ��
  ...         print item     # ���
  ...         break          # ��ֱ���˳�ѭ��
  ...
  5

��ʵ������������е�ѭ����Ҳ������ôд�ģ�::

  if item>=5:
      print item
      break


ǰ��˵���� ``for`` ��������Ը� ``else`` �Ӿ䣬������ ``else`` �Ӿ京���ǣ���� for һֱѭ������ĩβ
����������˳�ѭ������ô���ͻ�ִ������ ``else`` �Ӿ䣬�������� ``break`` �����쳣��ԭ���˳�ѭ���ģ�
�򲻻�ִ�� ``else`` �Ӿ䡣

��ʵ�ڳ��������Ǿͳ����ͻ����������ĳ�������ĳ���б���ÿһ��Ԫ��ִ��ĳ��������
����ɹ�ִ�������� ``break`` ����ѭ������������������б�����û��һ��Ԫ������Ҫ��
Ҳ������ζ�ű���ʧ�ܣ���ô����ʧ����������Ϳ��Է��� ``else`` �Ӿ����ˣ����磺
::

  >>> for item in range(10):
  ...     if item<10:
  ...         continue
  ...     else:
  ...         print item
  ...         break
  ... else:
  ...     print 'û�д��ڵ���10������'
  ...
  û�д��ڵ���10������

.. topic:: ���ַ��� ``for`` ���
 
  �������Ϥ c ���ԵĻ�����ῴ�� python �� for �� c �� for �Ĳ�ͬ��
  �����ϵ��﷨������Ȼ���׿�������ʵ�������ǵĺ���ȴ���и����Ĳ�ͬ�ġ�
  Ҫ��� python ������ʽ�� ``for`` ���Ļ�����ҿ�������ĳЩ���Ե� ``for in`` ���� ``foreach`` ֮����﷨��
  ::

    /* c ���� */
    for(int i=0; i<count; i++){
        ...
    }
    
    # python
    for item in a_iterable:
        ...
 
  �򵥵�˵�� c ������ʽ�� ``for`` ���Ĺ���ԭ���������ģ�ȡ��0������1������2����һֱȡ�����һ�������ӡ�
  �������������أ����ǶԵ�����ȡ��һ����ȡ��һ����ȡ��һ����һֱȡ���������Լ���ͣΪֹ��
  ʵ���� python �� ``for`` �����ͬʱ֧�������ַ��ġ�

  ������������һ�� python �� ``for`` ��䣺::

    for item in obj:
        ...

  ��� ``obj`` ����ʵ���� ``__iter__`` ������
  Ҳ����˵���Ǹ���������������ǵ��������� ``for`` ��䣬
  ��������δ���Ҳ�͵ȼ��ڣ�::

    iterator = iter(obj) # ��ȡ��������
    # iter(obj) �ȼ��� obj.__iter__()
    try:
        item = iterator.next() # ȡ��һ��
        ...
        item = iterator.next() # ȡ��һ��
        ...
    except StopIteration:      # ��������ͣ�ˣ��μ� �쳣����_ ��
        pass

  �������� ``obj`` ����ʵ���� ``__getitem__`` ������
  Ҳ����˵��֧��������������ͳ��� c ���Է������ֵ�������
  ��δ����ȼ��ڣ�::
    
    try:
      item = obj[0]      # ȡ��0��
      # obj[0] �ȼ��� obj.__getitem__(0)
      ...
      item = obj[1]      # ȡ��1��
      ...
    except StopIteration:      # ȡ�����һ���ˣ��μ� �쳣����_ ��
        pass

  ����ٲ���һ�ѣ�::

    >>> class Indexable(object):
    ...     def __getitem__(self, i):
    ...         if i>10:
    ...             raise StopIteration()
    ...         print 'get object %d'%i
    ...
    >>> class Iterable(object):
    ...     def __init__(self):
    ...         self.counter = 0
    ...     def __iter__(self):
    ...         return self
    ...     def next(self):
    ...         if self.counter>10:
    ...             raise StopIteration()
    ...         print 'get next, current is %d'%self.counter
    ...         self.counter += 1
    ...
    >>> container = Indexable()
    >>> for i in container:pass
    ...
    get object 0
    get object 1
    get object 2
    get object 3
    get object 4
    get object 5
    get object 6
    get object 7
    get object 8
    get object 9
    get object 10
    >>> container = Iterable()
    >>> for i in container:pass
    ...
    get next, current is 0
    get next, current is 1
    get next, current is 2
    get next, current is 3
    get next, current is 4
    get next, current is 5
    get next, current is 6
    get next, current is 7
    get next, current is 8
    get next, current is 9
    get next, current is 10

while ѭ��
============

��� for ��˵ while �ͼ򵥶��ˣ�::

  while not self.accepted_by(her):
      trace(her)

ֻҪ condition Ϊ True ��Ҳ����������������Ͳ�ִͣ������Ĵ��롣

�� while д��ѭ�����ǱȽϷ��㣺::

  while True:
      print 'running...'

�쳣����
============

��׽�쳣
---------

::
  
  try:
      code_block()
      ...
  except SomeException, e:
      do_some_thing_with_exception(e)
  except (Exception1, Exception2), e:
      do_some_thing_with_exception(e)
  except:
      do_some_thing_with_other_exceptions()
  else:
      do_some_thing_when_success()
  finally:
      do_some_thing()

�׳��쳣
--------

::

  raise SomeException("some reason")

�Զ����쳣
----------

::

  class MyException(Exception):
      ...

С��
==========

#. ѧϰ�˼������̿��Ƶ��﷨����� python �﷨��Ƶļ�ࡢ������

#. �˽�����ν�������ĸ���

#. ֪���� __getitem__ �������Ĺ�ϵ

#. �˽��쳣������׳��Ͳ���

��ϰ
===========

#. ʹ�� while �����ʾ���� for ���Ĺ��̡�

.. macro:: [[PageComment2(nosmiley=1, notify=1)]]

