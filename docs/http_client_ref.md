HTTP Client Reference
--------------------

All commands are accessed through the ``ipfshttpclient.Client`` class.

### Exceptions

```eval_rst
.. automodule:: ipfshttpclient.exceptions
    :members:
```


### Utility Functions

```eval_rst
.. data:: ipfshttpclient.DEFAULT_ADDR

  The default IPFS API daemon location the client library will attempt to
  connect to. By default this will have a value of ``multiaddr.Multiaddr("/dns/localhost/tcp/5001/http")``.
  
  This may be overwritten on a per-client-instance basis using
  the ``addr`` parameter of the :func:`~ipfshttpclient.connect` function.

.. data:: ipfshttpclient.DEFAULT_BASE

  The default HTTP URL path prefix (or “base”) that the client library will use.
  By default this will have a value of ``"api/v0"``.
  
  This may be overwritten on a per-client-instance basis using the ``base``
  parameter of the :func:`~ipfshttpclient.connect` function.

.. autofunction:: ipfshttpclient.connect(addr=DEFAULT_ADDR, base=DEFAULT_BASE)

.. autofunction:: ipfshttpclient.assert_version

```

### The API Client

All methods accept the following parameters in their `kwargs`:

 * **offline** ([*bool*](https://docs.python.org/3/library/functions.html#bool)) – Prevent the deamon from communicating with any remote IPFS node while performing the requested action?
 * **opts** ([*dict*](https://docs.python.org/3/library/stdtypes.html#dict)) – A mapping of custom IPFS API parameters to be sent along with the regular parameters generated by the client library
    * Values specified here will always override their respective counterparts
      of the client library itself.
 * **stream** ([*bool*](https://docs.python.org/3/library/functions.html#bool)) – Return results incrementally as they arrive?
    * Each method called with `stream=True` will return a generator instead
      of the documented value. If the return type is of type `list` then each
      item of the given list will be yielded separately; if it is of type
      `bytes` then arbitrary bags of bytes will be yielded that together form
      a stream; finally, if it is of type `dict` then the single dictonary item
      will be yielded once.
 * **timeout** ([*float*](https://docs.python.org/3/library/functions.html#float)) – The number of seconds to wait of a daemon reply before giving up

```eval_rst
.. autoclientclass:: ipfshttpclient.Client(addr=DEFAULT_ADDR, base=DEFAULT_BASE)
  :members:
  :inherited-members:
  :undoc-members:

```
