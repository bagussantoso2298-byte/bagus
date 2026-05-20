<!-- SIMPAN DENGAN NAMA : index.html -->

<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>

<title>Search SKU</title>

<style>

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    font-family:Arial, Helvetica, sans-serif;
    background:#0f172a;
    color:white;
    padding:20px;
}

.container{
    max-width:700px;
    margin:auto;
}

.title{
    text-align:center;
    margin-bottom:25px;
}

.title h1{
    font-size:35px;
    color:#38bdf8;
}

.title p{
    color:#94a3b8;
    margin-top:5px;
}

.search-box{
    margin-bottom:20px;
}

.search-box input{
    width:100%;
    padding:15px;
    border:none;
    border-radius:12px;
    font-size:18px;
    background:#1e293b;
    color:white;
    outline:none;
}

.card{
    background:#1e293b;
    padding:15px;
    border-radius:15px;
    margin-bottom:15px;
    border:1px solid #334155;
    transition:0.3s;
}

.card:hover{
    transform:scale(1.02);
    border-color:#38bdf8;
}

.nama{
    font-size:20px;
    font-weight:bold;
    margin-bottom:10px;
    color:#38bdf8;
}

.info{
    color:#cbd5e1;
    margin-top:5px;
}

.not-found{
    text-align:center;
    margin-top:30px;
    color:#f87171;
}

.footer{
    text-align:center;
    margin-top:30px;
    color:#64748b;
    font-size:14px;
}

</style>
</head>

<body>

<div class="container">

    <div class="title">
        <h1>SEARCH SKU</h1>
        <p>Pencarian SKU Produk Cepat</p>
    </div>

    <div class="search-box">
        <input 
            type="text" 
            id="search"
            placeholder="Cari SKU / Nama Produk..."
        >
    </div>

    <div id="result"></div>

    <div class="footer">
        Powered by GitHub Pages
    </div>

</div>

<script>

const data = [

{
    sku:"8991001001",
    nama:"Indomie Goreng",
    kategori:"Makanan",
    stok:"120"
},

{
    sku:"8991001002",
    nama:"Teh Botol Sosro",
    kategori:"Minuman",
    stok:"75"
},

{
    sku:"8991001003",
    nama:"Ultra Milk Coklat",
    kategori:"Susu",
    stok:"40"
},

{
    sku:"8991001004",
    nama:"Aqua 600ml",
    kategori:"Air Mineral",
    stok:"250"
}

];

const search = document.getElementById("search");
const result = document.getElementById("result");

function tampilkanData(keyword=""){

    result.innerHTML="";

    const filtered = data.filter(item =>

        item.nama.toLowerCase().includes(keyword.toLowerCase()) ||

        item.sku.toLowerCase().includes(keyword.toLowerCase())

    );

    if(filtered.length === 0){

        result.innerHTML = `
            <div class="not-found">
                Data tidak ditemukan
            </div>
        `;

        return;
    }

    filtered.forEach(item => {

        result.innerHTML += `

        <div class="card">

            <div class="nama">
                ${item.nama}
            </div>

            <div class="info">
                SKU : ${item.sku}
            </div>

            <div class="info">
                Kategori : ${item.kategori}
            </div>

            <div class="info">
                Stok : ${item.stok}
            </div>

        </div>

        `;
    });

}

search.addEventListener("keyup", () => {

    tampilkanData(search.value);

});

tampilkanData();

</script>

</body>
</html>
