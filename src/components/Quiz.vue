<template>
  <div id="quiz">
    <h1>Quiz</h1>
    <div v-for="(data, index) in soal">
      <p>{{index + 1}}. {{data.soalDeskripsi}} </p>
      <div v-for="(pilgan, indexPilgan) in data.pilihanGanda">
        <input type="radio" @click="checkJawaban(index, indexPilgan)" :value="pilgan[0]" :name="index">
        <span v-text="pilgan[0]"></span>
      </div>
    </div>
    <h4>Nilai Kamu : {{score}}</h4>
    <h4 v-if="score > 70">Mantap Lanjutkan!!</h4>
    <h4 v-else>Jangan Patah Semangat, Coba Lagi!!</h4>
  </div>
</template>

<script>

export default {
  name: 'quiz',
  data() {
    return {
      score : 0,
      jawabanBenar : [],
      jawabanSalah : [],
      soal : [
        {
          soalDeskripsi : "Siapakah Presiden Pertama Indonesia?",
          pilihanGanda : [
            ["Soekarno", true],
            ["Moh.Hatta"],
            ["Megawati"],
            ["Jokowi"]
          ]
        },
        {
          soalDeskripsi : "Dikota manakah bandung lautan api terjadi",
          pilihanGanda : [
            ["Yogyakarta"],
            ["Bali"],
            ["Malang"],
            ["Bandung", true]
          ]
        },
        {
          soalDeskripsi : "Tanggal Berapa Indonesia Merdeka?",
          pilihanGanda : [
            ["17 Agustus 1989"],
            ["17 Agustus 1955"],
            ["17 Agustus 1945", true],
            ["18 Agustus 1945"]
          ]
        },
        {
          soalDeskripsi : "Siapakah Pemimpin Gerakan DI/TII Di Jawabarat?",
          pilihanGanda : [
            ["Sekarmadji Maridjan Kartosuwiryo", true],
            ["Soekarno"],
            ["Moh.Hatta"],
            ["Sekarmidjan"]
          ]
        },
        {
          soalDeskripsi : "Yang Termasuk Bahasa Pemrograman, Kecuali....",
          pilihanGanda : [
            ["HTML", true],
            ["C"],
            ["Java"],
            ["Python"]
          ]
        },
        {
          soalDeskripsi : "Zat Hijau Pada Daun Disebut",
          pilihanGanda : [
            ["Fotosintesis"],
            ["Klorofil", true],
            ["Benang Sari"],
            ["Putik"]
          ]
        },
        {
          soalDeskripsi : " 19 + 10 * 91 * 0",
          pilihanGanda : [
            ["19", true],
            ["0"],
            ["91"],
            ["10"]
          ]
        },
        {
          soalDeskripsi : "Apa Itu SMK?",
          pilihanGanda : [
            ["Sekarmadji Maridjan Kartosuwiryo"],
            ["Sekolah Menengah Kejuruan", true],
            ["Sekolah Menengah Kebidanan"],
            ["Sekolah Menengah Kesana"]
          ]
        },
        {
          soalDeskripsi : "Siapa Pendiri Microsoft?",
          pilihanGanda : [
            ["Larry Pages"],
            ["Steve Jobs"],
            ["Gaben"],
            ["Bill Gates", true]
          ]
        },
        {
          soalDeskripsi : "Di kota mana facebook dikembangkan?",
          pilihanGanda : [
            ["Silicon Valley", true],
            ["Chicago"],
            ["Ohio"],
            ["Solo"]
          ]
        }
      ]
    }
  },
  methods : {
      checkJawaban(index, indexPilgan) {
        if(this.soal[index].pilihanGanda[indexPilgan][1]){
          if(this.jawabanBenar.indexOf(index) == -1){
            this.jawabanBenar.push(index);
          }
          if(this.jawabanSalah.indexOf(index) != -1){
            this.jawabanSalah.splice(this.jawabanSalah.indexOf(index),1);
          }
        }else{
          if(this.jawabanBenar.indexOf(index) != -1){
            this.jawabanBenar.splice(this.jawabanBenar.indexOf(index),1);
            this.jawabanSalah.push(index);
          }else if(this.jawabanSalah.indexOf(index) != -1){
  
          }else{
            this.jawabanSalah.push(index);
          }
        }
        this.score = this.jawabanBenar.length * 10;
      }
    }
}
</script>

<style scoped>

</style>