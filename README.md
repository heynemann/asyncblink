AsyncBlink is a small extention to Blinker and enables you to use
coroutines as receivers for your signals.

Install
=======

Installation is simple, via pip:

```sh
   $ pip install asyncblink
```


Usage
=====

Usage is simple, too. Create a signal, connect some receivers to it
and then use the ``send()`` method to trigger all receivers

```python
from asyncblink import signal
my_signal = signal('nice-signal')

@asyncio.coroutine
def coro_receiver(sender, **kwargs):
    # an expensive io operation here
    return 'done'

def receiver(sender):
    return 'ok'

my_signal.connect(coro_receiver)
my_signal.connect(receiver)
my_signal.send('some-sender')
```

In fact, AsyncBlink's usage is the same as Blinker, you simply can use
coroutines as receivers. Take a look at the
[Blinker documentation](http://pythonhosted.org/blinker/>) for
further information.


Source Code
===========

Source code is hosted on [gitlab](https://gitlab.com/jucacrispim/asyncblink).