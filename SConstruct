#! /usr/bin/env python
# -*- coding: utf-8 -*-
# vim:fenc=utf-8
#
# Copyright © 2019 hurricane <hurricane1026@gmail.com>
#


"""
Scons build script for google mock library
"""

from SCons.Script import *

if 'env' not in vars().keys():
    env = Environment()

#scripts = ['googletest/SConscript', 'googlemock/SConscript']
env.Append(CXXFLAGS = '-std=c++11')

Export('env')
#VariantDir('build_gtest', 'googletest')
SConscript('googletest/SConstruct', variant_dir = 'build_gtest', exports='env')
#SConscript('googletest/SConscript', exports='env')
SConscript('googlemock/SConstruct', variant_dir = 'build_gmock', exports='env')


