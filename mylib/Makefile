build_type_ = debug
build_dir_  = _build_$(build_type_)
deps_dir_   = ../_deps_$(build_type_)

rm:
	rm -rf $(build_dir_)

c: rm
	cmake -S . -B $(build_dir_) -D CMAKE_BUILD_TYPE=$(build_type_)

b: c
	cmake --build $(build_dir_) --config $(build_type_) --parallel

i: b
	cmake --install $(build_dir_) --config $(build_type_) --prefix $(deps_dir_)  



