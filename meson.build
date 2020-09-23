project('simple-cam', 'c', 'cpp',
	default_options : [
		'werror=true',
		'warning_level=2',
		'cpp_std=c++14',
	])

# simple-cam.cpp is the fully commented application
src_files = files([
	'simple-cam.cpp',
])

# Point your PKG_CONFIG_PATH environment variable to the
# libcamera install path camera.pc file ($prefix/lib/pkgconfig/camera.pc)
libcamera_deps = [
      dependency('camera', required : true),
]

cpp_arguments = [ '-Wno-unused-parameter', ]

add_project_arguments(cpp_arguments, language : 'cpp')

# simple-cam executable
simple_cam = executable('simple-cam', src_files,
                        dependencies : libcamera_deps)
