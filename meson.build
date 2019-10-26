project('elce-cam', 'c', 'cpp',
	default_options : [
		'werror=true',
		'-Wno-unused-parameter=true',
		'warning_level=2',
		'cpp_std=c++11',
	])

cc = meson.get_compiler('c')
config_h = configuration_data()

# elce-cam source files
# elce-cam.cpp is the fully commented application
# mini=elce.cpp is for live coding during ELC-E 2019
src_files = files([
	'elce-cam.cpp',
])

# Point your PKG_CONFIG_PATH environment variable to the
# libcamera install path camera.pc file ($prefix/lib/pkgconfig/camera.pc)
libcamera_deps = [
      dependency('camera', required : true),
]

cpp_arguments = '-Wno-unused-parameter'
add_project_arguments(cpp_arguments, language : 'cpp')

# elce-cam executable
elce_cam = executable('elce-cam', src_files,
		      dependencies : libcamera_deps,
		      install : false)
