import os
import subprocess
import sys
import time
Import('env')

# The return value is the collection of files installed in the build destination.
returnValue = []

# Add support for multiple build targets in the same workset
env.VariantDir('build', 'src', duplicate = 0)

prog = env.Install('$DISTDIR/lib', env.SConscript('build/SConscript', exports='env'))

returnValue += prog

Return('returnValue')