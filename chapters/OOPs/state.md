# State

#### **State <--> attributes**
In programming, state refers to the current condition or information held by an object at a given time.

> Just like our mood or health at a particular moment defines our state, an object’s state is defined by the values of its attributes.

An **attribute** is a **variable** or **property** inside an object that stores some information.

So essentially:

> **State = the collection of attribute values an object holds**.

Let’s take a house object.
* **Attributes**:
    * color = "blue"
    * rooms = 3
    * is_locked = True

This set of values defines the **state** of the house.

If we repaint it (`color = "white"`) or unlock it (`is_locked = False`), the **state has changed** — because the **attribute values have changed**.


**Think of a Person object**.

* **Attributes**:
    * name = "Narendra"
    * age = 75
    * mood = "happy"

So, the **state** of Narendra is:

> “A 75-year-old person named Narendra who is **happy**.”

If his mood becomes **sad**, the **state of the object has changed**.

#### Summary

| Concept             | Explanation                                        |
| ------------------- | -------------------------------------------------- |
| **Attribute**       | A variable inside an object (e.g., `color`, `age`) |
| **State**           | The combination of all current attribute values    |
| **Change in State** | Occurs when one or more attributes are updated     |



```python
import numpy as np
a  = np.array([1,2,3,4])
type(a)
```




    numpy.ndarray




```python
## State <--> attributes
a.shape
```




    (4,)



* Attributes (or states) in python objects are represented by variables, lik numbers, or strings or tuples, in the case of numpy array shape.
* attributes **<--> variables <-->** `obj.my_attribute`


```python
dir(a) # list all attributes and methods
```




    ['T',
     '__abs__',
     '__add__',
     '__and__',
     '__array__',
     '__array_finalize__',
     '__array_function__',
     '__array_interface__',
     '__array_namespace__',
     '__array_priority__',
     '__array_struct__',
     '__array_ufunc__',
     '__array_wrap__',
     '__bool__',
     '__class__',
     '__class_getitem__',
     '__complex__',
     '__contains__',
     '__copy__',
     '__deepcopy__',
     '__delattr__',
     '__delitem__',
     '__dir__',
     '__divmod__',
     '__dlpack__',
     '__dlpack_device__',
     '__doc__',
     '__eq__',
     '__float__',
     '__floordiv__',
     '__format__',
     '__ge__',
     '__getattribute__',
     '__getitem__',
     '__gt__',
     '__hash__',
     '__iadd__',
     '__iand__',
     '__ifloordiv__',
     '__ilshift__',
     '__imatmul__',
     '__imod__',
     '__imul__',
     '__index__',
     '__init__',
     '__init_subclass__',
     '__int__',
     '__invert__',
     '__ior__',
     '__ipow__',
     '__irshift__',
     '__isub__',
     '__iter__',
     '__itruediv__',
     '__ixor__',
     '__le__',
     '__len__',
     '__lshift__',
     '__lt__',
     '__matmul__',
     '__mod__',
     '__mul__',
     '__ne__',
     '__neg__',
     '__new__',
     '__or__',
     '__pos__',
     '__pow__',
     '__radd__',
     '__rand__',
     '__rdivmod__',
     '__reduce__',
     '__reduce_ex__',
     '__repr__',
     '__rfloordiv__',
     '__rlshift__',
     '__rmatmul__',
     '__rmod__',
     '__rmul__',
     '__ror__',
     '__rpow__',
     '__rrshift__',
     '__rshift__',
     '__rsub__',
     '__rtruediv__',
     '__rxor__',
     '__setattr__',
     '__setitem__',
     '__setstate__',
     '__sizeof__',
     '__str__',
     '__sub__',
     '__subclasshook__',
     '__truediv__',
     '__xor__',
     'all',
     'any',
     'argmax',
     'argmin',
     'argpartition',
     'argsort',
     'astype',
     'base',
     'byteswap',
     'choose',
     'clip',
     'compress',
     'conj',
     'conjugate',
     'copy',
     'ctypes',
     'cumprod',
     'cumsum',
     'data',
     'device',
     'diagonal',
     'dot',
     'dtype',
     'dump',
     'dumps',
     'fill',
     'flags',
     'flat',
     'flatten',
     'getfield',
     'imag',
     'item',
     'itemset',
     'itemsize',
     'mT',
     'max',
     'mean',
     'min',
     'nbytes',
     'ndim',
     'newbyteorder',
     'nonzero',
     'partition',
     'prod',
     'ptp',
     'put',
     'ravel',
     'real',
     'repeat',
     'reshape',
     'resize',
     'round',
     'searchsorted',
     'setfield',
     'setflags',
     'shape',
     'size',
     'sort',
     'squeeze',
     'std',
     'strides',
     'sum',
     'swapaxes',
     'take',
     'to_device',
     'tobytes',
     'tofile',
     'tolist',
     'tostring',
     'trace',
     'transpose',
     'var',
     'view']


