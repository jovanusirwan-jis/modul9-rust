a. Apa itu AMQP?

AMQP adalah singkatan dari Advanced Message Queuing Protocol.
AMQP merupakan protokol komunikasi yang digunakan untuk mengirim pesan antar aplikasi atau antar service.

AMQP sering digunakan pada software seperti RabbitMQ untuk:

komunikasi asynchronous,
message queue (antrian pesan),
sistem terdistribusi,
microservices.

Dengan AMQP, sebuah aplikasi bisa mengirim pesan ke queue, lalu aplikasi lain bisa mengambil dan memproses pesan tersebut nanti.

Contoh:

Service A mengirim data pesanan.
Data masuk ke queue.
Service B mengambil dan memproses data tersebut.

Hal ini membuat sistem lebih stabil dan scalable.

b. Arti dari guest:guest@localhost:5672

Itu biasanya adalah bagian dari connection string untuk terhubung ke server AMQP seperti RabbitMQ.

Penjelasannya:

guest : guest @ localhost : 5672
1. guest pertama

Merupakan username untuk login.

2. guest kedua

Merupakan password dari user tersebut.

Jadi:

username = guest
password = guest
 
3. localhost

localhost berarti server berjalan di komputer yang sama dengan aplikasi yang digunakan.

Biasanya localhost mengarah ke:

127.0.0.1

yaitu alamat komputer sendiri.

4. 5672

Angka 5672 adalah port yang digunakan oleh AMQP/RabbitMQ untuk komunikasi.

Port bisa dianggap seperti “jalur komunikasi” agar aplikasi dapat terhubung ke server RabbitMQ.

Jadi secara keseluruhan:

guest:guest@localhost:5672

berarti: Menghubungkan aplikasi ke server RabbitMQ di komputer sendiri (localhost) melalui port 5672 menggunakan username guest dan password guest.

a. How much data will the publisher program send to the message broker in one run?

Program publisher tersebut akan mengirim 5 message/event ke message broker (RabbitMQ).

Hal ini karena terdapat 5 pemanggilan:

p.publish_event(...)

yaitu untuk data:

Amir
Budi
Cica
Dira
Emir

Jadi dalam satu kali program dijalankan:

Total message sent = 5 messages

Semua message tersebut dikirim ke event/queue "user_created".

b. The URL “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?

Itu berarti publisher dan subscriber terhubung ke RabbitMQ server yang sama.

Penjelasannya:

amqp://guest:guest@localhost:5672

memiliki arti:

amqp:// → menggunakan protokol AMQP
guest pertama → username
guest kedua → password
localhost → server RabbitMQ berjalan di komputer yang sama
5672 → port RabbitMQ

Karena URL pada publisher dan subscriber sama, maka:

publisher mengirim message ke RabbitMQ yang sama,
subscriber menerima message dari RabbitMQ yang sama.

Dengan begitu subscriber dapat menerima event yang dikirim publisher.