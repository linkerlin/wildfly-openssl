
SRC = alpn.c clientcert.c options.c session.c ssl.c threads.c util.c
OBJ = $(patsubst %.c, target/%.o, $(SRC))

default: target/classes/linux-i686/libwfssl.so

clean:
	rm -rf target

target/classes/linux-i686:
	mkdir -p target/classes/linux-i686

target/%.o : ../libwfssl/src/%.c target/classes/linux-i686
	cc -m32 -fPIC -c $< -o $@ -I../libwfssl/include -I$(JAVA_HOME)/include -I$(JAVA_HOME)/include/linux

target/classes/linux-i686/libwfssl.so: $(OBJ)
	cc -m32 -shared $(OBJ) -o $@ -Wl,--no-as-needed -ldl
