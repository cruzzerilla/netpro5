# Tugas 5

## Anggota
1. Aditya Eka Bagaskara (1301164222)
2. Ilham Ibnu Purnomo (1301164089)
3. Adisca Naufal Ristanto(1301164358)

## JSON Marshal
### Source Code
```go
package main
import (
	"encoding/json"
	"fmt"
)

type Person struct {
	FirstName string `json:"firstName"`
	LastName string `json:"lastName"`
}

func main() {
	bytes, err := json.Marshal(Person{
		FirstName: "John",
		LastName: "Dow",
	})
	if err != nil {
		panic(err)
	}

	fmt.Println(string(bytes))
}
```
### Penjelasan
Person Struct pada variabel bytes diinisialisasi atribut firstname “John” dan lastname “Dow”. Kemudian bytes diserialisasikan kedalam bentuk JSON dan diprint dengan keluaran Person struct dalam JSON

### Screenshot
![alt screenshot1][1]

## JSON Unmarshal
### Source Code
```go
package main
import (
	"encoding/json"
	"fmt"
)

type Person struct {
	FirstName string `json:"firstName"`
	LastName string `json:"lastName"`
}

func main() {
	in := `{"firstName":"John","lastName":"Dow"}`
	bytes := []byte(in)

	var p Person
	err := json.Unmarshal(bytes, &p)
	if err != nil {
		panic(err)
	}

	fmt.Printf("%+v", p)
	fmt.Println()
}

```
### Penjelasan
- Membuat struct dengan nama “Person” dalam bentuk JSON
- Assign firstname “John” dan lastname “Dow” dan disimpan dalam variable in.
- Variable in diubah menjadi bytes dalam type data []byte
- Variable bytes di decode dari JSON menjadi struct Person, lalu ditampung dalam variable p
- Print variable p

### Screenshot
![alt screenshot2][2]

## GRPC
### 1. Output
![alt screenshot3][3]
### 2. Cara Kerja & Diagram FSM
![alt fsm][4]
### 3. Analisis Perbedaan dari Protocol Buffer dan Flatbuffer
Protobuf
- Protocol Buffer memisahkan representasi in-memory dengan wire protocol.
- Protobuf merupakan metode untuk serialisasi data terstruktur.
- Saat objek protobuf dikembalikan, dilakukan parsing dan serialisasi kembali.

Flatbuffer
- Flatbuffer tidak memisahkan representasi in-memory dengan wire protocol.
- Flatbuffer melakukan serialisasi pada saat pembuatan objek pada representasi in-memory.
- Pada saat flatbuffer dikembalikan, yang ditampilkan hanya pointer

[1]: screenshot/marshal.png
[2]: screenshot/unmarshal.png
[4]: screenshot/grpc.png
[3]: screenshot/fsm.png