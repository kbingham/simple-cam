project('elce-cam', 'c', 'cpp',
	default_options : [
		'werror=true',
		'warning_level=2',
		'cpp_std=c++11',
	])

cc = meson.get_compiler('c')
config_h = configuration_data()

# elce-cam source files
src_files = files([
	'main.cpp',
])

# Point your PKG_CONFIG_PATH environment variable to the
# libcamera install path camera.pc file ($prefix/lib/pkgconfig/camera.pc)
libcamera_deps = [
      dependency('camera', required : true),
]

# elce-cam executable
elce_cam = executable('elce-cam', src_files,
		      dependencies : libcamera_deps,
		      install : false)
