import os

def _newEnvironment():
	e = Environment(CPPPATH=[], LIBPATH=[], LIBS=[], SHLIBSUFFIX='.so', SHLINKFLAGS=[ '$LINKFLAGS', '-shared' ], ENV=os.environ, **ARGUMENTS)
	e.AppendUnique(CFLAGS=os.environ.get('CFLAGS', '').split())
	e.AppendUnique(CXXFLAGS=os.environ.get('CXXFLAGS', '').split())
	for l in os.environ.get('LDFLAGS', '').split():
		if l.startswith('-L'):
			e.AppendUnique(LIBPATH=l[2:])
	e.createEnvironment = _newEnvironment
	return e

env = _newEnvironment()

# Defines needed for AllJoyn headers
env.Append(CXXFLAGS=Split('-DQCC_OS_GROUP_POSIX -DQCC_OS_LINUX'))
env.PrependUnique(LIBS = ['alljoyn_about', 'alljoyn', 'crypto', 'stdc++', 'pthread'])

env.SConscript('SConscript', exports='env')