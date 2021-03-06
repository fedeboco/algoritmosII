CXXARGS  = -g -Wall
CXXFLAGS = -I. $(CXXARGS)

all: tp1.exe

tp1.exe: main.cc cmdline.cc diccionario.cc arreglo.cc simbolo.cc compresion.cc funciones_impresion.cc funciones_impresion.h compresion.h diccionario.h arreglo.h simbolo.h cmdline.h tipos_datos.h
	$(CXX) $(CXXFLAGS) -o tp1.exe cmdline.cc main.cc diccionario.cc arreglo.cc simbolo.cc compresion.cc funciones_impresion.cc

clean:
	$(RM) -vf *.o *.exe *.t *.out *.err

valgrind: 
	for numero in 1 2 3 4 5 6 7 8 9 10; do \
	echo \ ;\
	echo TEST NÚMERO $$numero ----------------------;\
	rm test_valgrind.txt;\
	touch test_valgrind.txt;\
	valgrind ./tp1.exe -p compress -i "./tests/entrada$${numero}.txt" -o "./tests/salida$${numero}.txt";\
	valgrind ./tp1.exe -p decompress -i "./tests/salida$${numero}.txt" -o "./tests/vuelta$${numero}.txt";\
	echo \ ;\
	done
	
valgrind_log: 
	for numero in 1 2 3 4 5 6 7 8 9 10; do \
	echo \ ;\
	echo TEST NÚMERO $$numero ----------------------;\
	valgrind --log-file="./valgrind_tests/test_valgrind_normal_$${numero}.txt" ./tp1.exe -p compress -i "./tests/entrada$${numero}.txt" -o "./tests/salida$${numero}.txt";\
	valgrind --log-file="./valgrind_tests/test_valgrind_list_$${numero}.txt" ./tp1.exe -m list -p compress -i "./tests/entrada$${numero}.txt" -o "./tests/salida$${numero}.txt";\
	valgrind --log-file="./valgrind_tests/test_valgrind_tree_$${numero}.txt" ./tp1.exe -m tree -p compress -i "./tests/entrada$${numero}.txt" -o "./tests/salida$${numero}.txt";\
	valgrind --log-file="./valgrind_tests/test_valgrind_decompress_$${numero}.txt" ./tp1.exe -p decompress -i "./tests/salida$${numero}.txt" -o "./tests/vuelta$${numero}.txt";\
	echo \ ;\
	done
	valgrind --log-file="./valgrind_tests/test_big_list_compress.txt" ./tp1.exe -p compress -i "./tests/entrada_big.txt" -o "./tests/salida_big.txt" -m list ;\
	valgrind --log-file="./valgrind_tests/test_big_list_decompress.txt" ./tp1.exe -p decompress -i "./tests/salida_big.txt" -o "./tests/vuelta_big.txt" -m tree ;\
	valgrind --log-file="./valgrind_tests/test_big_tree_compress.txt" ./tp1.exe -p compress -i "./tests/entrada_big.txt" -o "./tests/salida_big.txt" -m tree ;\
	valgrind --log-file="./valgrind_tests/test_big_tree_decompress.txt" ./tp1.exe -p decompress -i "./tests/salida_big.txt" -o "./tests/vuelta_big.txt" -m tree ;\

test:
	for numero in 1 2 3 4 5 6 7 8 9 10; do \
	echo \ ;\
	echo TEST NÚMERO $$numero ----------------------;\
	./tp1.exe -p compress -i "./tests/entrada$${numero}.txt" -o "./tests/salida$${numero}.txt" ;\
	./tp1.exe -p decompress -i "./tests/salida$${numero}.txt" -o "./tests/vuelta$${numero}.txt" ;\
	diff -q -s "./tests/vuelta$${numero}.txt" "./tests/entrada$${numero}.txt" ;\
	echo \ ;\
	done

test_list:
	for numero in 1 2 3 4 5 6 7 8 9 10; do \
	echo \ ;\
	echo TEST NÚMERO $$numero ----------------------;\
	./tp1.exe -p compress -i "./tests/entrada$${numero}.txt" -o "./tests/salida$${numero}.txt" -m list;\
	./tp1.exe -p decompress -i "./tests/salida$${numero}.txt" -o "./tests/vuelta$${numero}.txt" -m list;\
	diff -q -s "./tests/vuelta$${numero}.txt" "./tests/entrada$${numero}.txt" ;\
	echo \ ;\
	done

test_tree:
	for numero in 1 2 3 4 5 6 7 8 9 10; do \
	echo \ ;\
	echo TEST NÚMERO $$numero ----------------------;\
	./tp1.exe -p compress -i "./tests/entrada$${numero}.txt" -o "./tests/salida$${numero}.txt" -m tree;\
	./tp1.exe -p decompress -i "./tests/salida$${numero}.txt" -o "./tests/vuelta$${numero}.txt" -m tree;\
	diff -q -s "./tests/vuelta$${numero}.txt" "./tests/entrada$${numero}.txt" ;\
	echo \ ;\
	done

test_big:
	echo TEST DE ARCHIVO GRANDE ;\
	./tp1.exe -p compress -i "./tests/entrada_big.txt" -o "./tests/salida_big.txt" ;\
	./tp1.exe -p decompress -i "./tests/salida_big.txt" -o "./tests/vuelta_big.txt" ;\
	diff -q -s "./tests/entrada_big.txt" "./tests/vuelta_big.txt" ;\
	echo \ ;\

test_big_list:
	echo TEST DE ARCHIVO GRANDE ;\
	./tp1.exe -p compress -i "./tests/entrada_big.txt" -o "./tests/salida_big.txt" -m list ;\
	./tp1.exe -p decompress -i "./tests/salida_big.txt" -o "./tests/vuelta_big.txt" -m list ;\
	diff -q -s "./tests/entrada_big.txt" "./tests/vuelta_big.txt" ;\
	echo \ ;\

test_big_tree:
	echo TEST DE ARCHIVO GRANDE ;\
	./tp1.exe -p compress -i "./tests/entrada_big.txt" -o "./tests/salida_big.txt" -m tree ;\
	./tp1.exe -p decompress -i "./tests/salida_big.txt" -o "./tests/vuelta_big.txt" -m tree ;\
	diff -q -s "./tests/entrada_big.txt" "./tests/vuelta_big.txt" ;\
	echo \ ;\
