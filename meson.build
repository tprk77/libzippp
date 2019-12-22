project(
  'libzippp',
  'cpp',
  version : '1.2.11',
  license : 'BSD3'
)

# Use static linking on Windows, and use BCrypt
libzip_dep_static = false
bcrypt_dep_opt = []
if build_machine.system() == 'windows'
  libzip_dep_static = true
  bcrypt_dep_opt = [meson.get_compiler('cpp').find_library('bcrypt')]
endif

# Technically, I think this wants 1.5.2... Does it matter?
libzip_dep = dependency('libzip', fallback : ['libzip', 'libzip_dep'], static : libzip_dep_static)

libzippp_src = [
  'src/libzippp.cpp',
  'src/libzippp.h'
]

# Always build this as a static library on Linux and Windows
libzippp_lib = static_library(
  'zippp',
  libzippp_src,
  dependencies : [libzip_dep] + bcrypt_dep_opt
)

libzippp_incdir = include_directories('src')

libzippp_dep = declare_dependency(
  version : meson.project_version(),
  include_directories : libzippp_incdir,
  link_with : libzippp_lib
)
