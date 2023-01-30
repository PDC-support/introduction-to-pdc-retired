CFLAGS=-fopenmp
HIPFLAGS=--offload-arch=gfx90a
TARGET=hello_world

tegner:
	$(eval CC := gcc)
	$(eval OPENMP_CC := mpicc)

beskow:
	$(eval CC := cc)
	$(eval OPENMP_CC := cc)

dardel:
	$(eval CC := cc)
	$(eval OPENMP_CC := cc)
	$(eval GPU_CC := hipcc)

all: hello_world openmp mpi gpu

hello_world:
	$(CC) -o $(TARGET) $(TARGET).c
	
openmp:
	$(OPENMP_CC) $(CFLAGS) -o $(TARGET)_openmp $(TARGET)_openmp.c
	
mpi:
	$(OPENMP_CC) $(CFLAGS) -o $(TARGET)_mpi $(TARGET)_mpi.c	

gpu:
	$(GPU_CC) $(HIPFLAGS) -o $(TARGET)_gpu $(TARGET)_gpu.cpp

clean:
	rm -f $(TARGET) $(TARGET)_mpi $(TARGET)_openmp $(TARGET)_gpu
