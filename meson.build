project('archive-d', 'd',
    meson_version: '>=0.46',
    license: 'BSL-1.0',
    version: '0.6.0'
)

project_soversion    = '0'

src_dir = include_directories('source/')
pkgc = import('pkgconfig')

archive_src = [
    'source/archive/core.d',
    'source/archive/tar.d',
    'source/archive/targz.d',
    'source/archive/zip.d',
]
install_subdir('source/archive/', install_dir: 'include/d/archive-d/')

archive_lib = library('archive-d',
        [archive_src],
        include_directories: [src_dir],
        install: true,
        version: meson.project_version(),
        soversion: project_soversion
)

pkgc.generate(name: 'archive-d',
              libraries: archive_lib,
              subdirs: 'd/archive-d/',
              version: meson.project_version(),
              description: 'An archive library that supports zip, tar, and targz written entirely in D.'
)

# for use by others which embed this as subproject
archive_dep = declare_dependency(
    link_with: [archive_lib],
    include_directories: [src_dir]
)
