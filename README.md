# RestFull-Oracle-Android

Sebelumnya diharapkan untuk membaca versi web 

- Github [Link](https://github.com/advenkris37/RestFull-Oracle-CodeIgniter).

--------------------

### Koneksi

Kamu perlu merubah koneksi ke Database RestFull Api pada **UtilsApi** pada bagian **BASE_URL_API**

```java
public class UtilsApi {

    public static final String BASE_URL_API = "http://192.168.1.14:8888/apex/obe/";

    public static BaseApiService getAPIService(){
        return RetrofitClient.getClient(BASE_URL_API).create(BaseApiService.class);
    }
}
```

Juga pada bagian **res/layout/xml/network_security_config.xml**

```xml
<network-security-config>
    <domain-config cleartextTrafficPermitted="true">
        <domain includeSubdomains="true">192.168.1.14</domain>
    </domain-config>
</network-security-config>
```

---------------

### Api Service

Rubah sesuai kebutuhan kalian untuk Request RestFull datanya pada **BaseApiService**

```java
public interface BaseApiService {

    @GET("barang")
    Call<ResponseBarang> getSemuaBarang();
}
```

-------------

### Extra Data

```java
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Spinner spin = (Spinner) findViewById(R.id.spinner);
        TextView nama = (TextView) findViewById(R.id.namabarang);
        TextView jenis = (TextView) findViewById(R.id.jenisbarang);
        TextView jumlah = (TextView) findViewById(R.id.jumlahbarang);
        TextView harga = (TextView) findViewById(R.id.hargabarang);
        mContext = this;
        mApiService = UtilsApi.getAPIService();
```

### Screenshoot

![gambar Get Product](https://github.com/advenkris37/RestFull-Oracle-Android/blob/master/ss.png)

