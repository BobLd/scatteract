SHELL := /bin/bash

.PHONY: all
all:
	pip install runcython
	makecython++ stitch_wrapper.pyx "" "stitch_rects.cpp ./hungarian/hungarian.cpp"

	cd hungarian && \
	TF_INC=$$(python -c 'import tensorflow as tf; print(tf.sysconfig.get_include())') && \
	if [ `uname` == Darwin ];\
	then g++ -std=c++11 -shared hungarian.cc -o hungarian.so -fPIC -I $$TF_INC -undefined dynamic_lookup;\
	else g++ -std=c++11 -shared hungarian.cc -o hungarian.so -fPIC -I  $$TF_INC; fi
