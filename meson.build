project(
  'libzippp',
  'cpp',
  version : '1.2.11',
  license : 'BSD3'
)

# Technically, I think this wants 1.5.2... Does it matter?
libzip_dep = dependency('libzip', fallback : ['libzip', 'libzip_dep'])

libzippp_src = [
  'src/libzippp.cpp',
  'src/libzippp.h'
]

libzippp_lib = library(
  'zippp',
  libzippp_src,
  dependencies : [libzip_dep]
)

libzippp_incdir = include_directories('src')

libzippp_dep = declare_dependency(
  version : meson.project_version(),
  include_directories : libzippp_incdir,
  link_with : libzippp_lib
)
