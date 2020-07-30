objects = double_array_trie.o utils.o

double_array_trie: $(objects)
	$(CPP) $(CPPFLAGS) -o double_array_trie $(objects)

double_array_trie.o: 
utils.o:

.PHONY: clean
clean:
	rm $(objects)

CPP=g++
# for macos
# LDFLAGS="-Wl,-rpath,/PATH/TO/LIB/lib/python3.7/site-packages/pydat"
CPPFLAGS=-std=c++11 -g