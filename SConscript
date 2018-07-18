
import os
import rtconfig
from building import *

cwd = GetCurrentDir()
coap_src_dir = cwd + '/libcoap/src'

src = Split('''
libcoap/src/address.c
libcoap/src/async.c
libcoap/src/block.c
libcoap/src/coap_time.c
libcoap/src/debug.c
libcoap/src/encode.c
libcoap/src/hashkey.c
libcoap/src/mem.c
libcoap/src/net.c
libcoap/src/option.c
libcoap/src/pdu.c
libcoap/src/resource.c
libcoap/src/str.c
libcoap/src/subscribe.c
libcoap/src/uri.c
coap-rtthread/coap_io_rt.c
''')

CPPPATH = [cwd + '/libcoap/include']
CPPPATH += [cwd + '/libcoap/include/coap']
CPPPATH += [cwd + '/coap-rtthread']
CPPPATH += [cwd + '/coap-rtthread/include']

CPPDEFINES = ['WITH_POSIX']

LOCAL_CCFLAGS = ''

if rtconfig.CROSS_TOOL == 'keil':
    LOCAL_CCFLAGS += ' --gnu'

group = DefineGroup('coap', src, depend = ['PKG_USING_COAP'], CPPPATH = CPPPATH, LOCAL_CCFLAGS = LOCAL_CCFLAGS, CPPDEFINES = CPPDEFINES)

examples_src = Split('''
examples/coap_client.c
examples/coap_server.c
''')

group = group + DefineGroup('coap-examples', examples_src, depend = ['PKG_USING_COAP_EXAMPLE', 'PKG_USING_COAP'], CPPPATH = CPPPATH)

Return('group')
