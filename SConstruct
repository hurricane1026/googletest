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
env.Append(CXXFLAGS = '-Wall')
env.Append(CXXFLAGS = '-Werror')
env.Append(CXXFLAGS = '-Wextra')
env.Append(CXXFLAGS = '-Wendif-labels')
env.Append(CXXFLAGS = '-Wnewline-eof')
env.Append(CXXFLAGS = '-Wshadow')
env.Append(CXXFLAGS = '-Wno-sign-compare')
env.Append(TARGET_ARCH = 'x86_64')
env.AppendUnique(CCFLAGS = '-pthread')
env.AppendUnique(LINKFLAGS = '-pthread')
env.Append(CCFLAGS='-DDEBUG')
env.Append(CCFLAGS='-g')
env.Append(CCFLAGS='-O0')

#VariantDir('build_gtest', 'googletest')
#SConscript('googletest/SConscript', exports='env')

gtest_env = env.Clone()
gmock_env = env.Clone()

VariantDir('build_gtest', './googletest/', duplicate = 0)
VariantDir('build_gmock', './googlemock/', duplicate = 0)

#gtest_env.AppendUnique(CPPPATH = ['#/googletest'])
gtest_env.AppendUnique(CPPPATH = ['#/googletest/include'])
gtest_env.AppendUnique(CPPPATH = ['#/googletest'])

gmock_env.AppendUnique(CPPPATH = ['./googlemock/include'])
gmock_env.AppendUnique(CPPPATH = ['./googlemock'])
gmock_env.AppendUnique(CPPPATH = ['./googletest/include'])

gmock_env.AppendUnique(LIBPATH = ['#/libs/'])
gmock_env.AppendUnique(LIBS = ['-lgtest'])

gtest_obj = gtest_env.SharedLibrary('libs/gtest', '#/googletest/src/gtest-all.cc')

gmock_obj = gmock_env.SharedLibrary('libs/gmock', '#/googlemock/src/gmock-all.cc')

Depends(gmock_obj, gtest_obj)
