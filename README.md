# APLIKASI MOXFLIX
MoxFlix adalah aplikasi Android sederhana yang dirancang untuk membantu pengguna menemukan dan melihat keterangan lengkap tentang berbagai film. Dengan antarmuka yang sederhana dan mudah digunakan, MoxFlix menyediakan informasi penting seperti sinopsis, genre, tahun rilis, durasi, dan rating film.

## Features

- Dapat memberikan informasi terkait film seperti 
judul,Rating Film,Tahun Rilis,Sutradara,dan Sinopsis



## Tech

Aplikasi ini dibangun dengan menggunakan:
- Android Studio dolphin
- Emulator
- Bahasa pemrograman Java
- Gradle setting :
    implementation 'androidx.appcompat:appcompat:1.4.0'
    implementation 'com.google.android.material:material:1.5.0'

## Structure
Dibawah ini Merupakan folder dan sub folder yang digunakan dalam merancang aplikasi MoxFlix. Dalam merancang Aplikasi ini saya menggunakan 4 java class dan 4file berjenis xml. Berikut tampilannya:
![Uploading struktur.png…]()

## Installation
1. Untuk menginstal aplikasi ini, kamu bisa mendownload file pada folder PPM.ZIP diatas
2. setelah mendownload filenya, extract file ZIP tersebut kemudian import kedalam android studio.




## Development
Pada tahap ini saya akan menjabarkan fungsi dari file yang digunakan dalam perancangan aplikasi MoxFix ini:
### Java Class
#### SharedViewModel.java:
SharedViewModel memungkinkan Fragment untuk berbagi dan berkomunikasi tanpa harus secara langsung berinteraksi satu sama lain. Hal ini penting dalam kasus di mana beberapa Fragment dalam satu Activity membutuhkan data yang sama atau hasil dari suatu operasi.Berikut tampilan Sortcutnya:

```sh
package com.example.ppm2;

import androidx.lifecycle.LiveData;
import androidx.lifecycle.MutableLiveData;
import androidx.lifecycle.ViewModel;

public class SharedViewModel extends ViewModel {

    private final MutableLiveData<String> selectedItem = new MutableLiveData<>();

    public void selectItem(String item) {
        selectedItem.setValue(item);
    }

    public LiveData<String> getSelectedItem() {
        return selectedItem;
    }
}
```

#### FragmentA.java:Fragment A berfungsi sebagai pengirim data atau sebagai tempat di mana interaksi pertama dengan pengguna terjadi. Fragment ini sering kali berisi elemen UI yang mengumpulkan input dari pengguna atau memungkinkan pengguna untuk melakukan aksi tertentu (seperti menekan tombol atau memilih item dari daftar).Berikut Tampilan Shortcutnya:


```sh
package com.example.ppm2;

import android.os.Bundle;

import androidx.fragment.app.Fragment;
import androidx.lifecycle.ViewModelProvider;

import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.Button;

/**
 * A simple {@link Fragment} subclass.
 * Use the {@link FragmentA#newInstance} factory method to
 * create an instance of this fragment.
 */
public class FragmentA extends Fragment {
    private SharedViewModel sharedViewModel;

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
        View view = inflater.inflate(R.layout.fragment_a, container, false);
        sharedViewModel = new ViewModelProvider(requireActivity()).get(SharedViewModel.class);

        Button btnTGS = view.findViewById(R.id.btnTGS);
        btnTGS.setOnClickListener(v -> {
            sharedViewModel.selectItem(" RATING 4.8 "+"\n"+"Tahun 2017"+"\n"+"Sutradara Michael Gracey"+"\n"+"Sinopsis:Film ini menceritakan kisah tentang PT Barnum (Hugh Jackman) yang diberhentikan dari perusahaannya yang akan bangkrut. Barnum pun berpikir meminjam uang dari bank untuk membeli sebuah museum dimana museum tersebut memajang berbagai macam patung lilin.\n" +
                    "\n" +
                    "\n" +
                    "Sayangnya penjualan tiket museum sangat rendah. Di tengah sepi pengunjung museum, sang anak pun memberikan ide untuk mempertunjukkan sesuatu yang hidup untuk museumnya. Saat itulah ia mulai bertemu dengan banyak pemain untuk bisa bergabung dalam pertunjukkan sirkusnya.");
        });

        Button btnBC = view.findViewById(R.id.btnBC);
        btnBC.setOnClickListener(v -> {
            sharedViewModel.selectItem("Rating 4.8"+"\n"+"Tahun 2015"+"\n"+"Sutradara Tatsuya Yoshihara"+"\n"+"Sinopsis : Black Clover adalah serial manga dan anime bergenre fantasi yang bercerita tentang Asta dan Yuno, dua anak laki-laki yang berjuang untuk menjadi Raja Penyihir di dunia sihir");
        });

        Button btnAVATAR = view.findViewById(R.id.btnAVATAR);
        btnAVATAR.setOnClickListener(v -> {
            sharedViewModel.selectItem("Rating 4.3"+"\n"+"Tahun 2022"+"\n"+"Sutradara Cameron"+"\n"+"Sinopsis : Avatar 2 menceritakan perjalanan keluarga lima anak Jake Sully dan Neytiri yang baru ditemukan. Terlepas dari upaya terbaik mereka untuk menjaga keluarga mereka tetap bersama. \n" +
                    "\n" +
                    "Akan tetapi, ancaman yang akrab muncul kembali dan memaksa Jake, Neytiri, dan anak-anak mereka untuk melarikan diri ke tanah klan Metkayina di lautan Pandora. ");
        });

        return view;
    }
    // TODO: Rename parameter arguments, choose names that match
    // the fragment initialization parameters, e.g. ARG_ITEM_NUMBER
    private static final String ARG_PARAM1 = "param1";
    private static final String ARG_PARAM2 = "param2";

    // TODO: Rename and change types of parameters
    private String mParam1;
    private String mParam2;

    public FragmentA() {
        // Required empty public constructor
    }

    /**
     * Use this factory method to create a new instance of
     * this fragment using the provided parameters.
     *
     * @param param1 Parameter 1.
     * @param param2 Parameter 2.
     * @return A new instance of fragment FragmentA.
     */
    // TODO: Rename and change types and number of parameters
    public static FragmentA newInstance(String param1, String param2) {
        FragmentA fragment = new FragmentA();
        Bundle args = new Bundle();
        args.putString(ARG_PARAM1, param1);
        args.putString(ARG_PARAM2, param2);
        fragment.setArguments(args);
        return fragment;
    }

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        if (getArguments() != null) {
            mParam1 = getArguments().getString(ARG_PARAM1);
            mParam2 = getArguments().getString(ARG_PARAM2);
        }
    }


}
```

#### FragmentB.java:Fragment B biasanya berfungsi sebagai penerima data yang dikirim dari Fragment A, dan menampilkan data tersebut kepada pengguna. Ini juga bisa berfungsi untuk menampilkan informasi lebih rinci berdasarkan pilihan atau interaksi yang dilakukan di Fragment A.Berikut tampilan Shortcutnya:


```sh
package com.example.ppm2;

import android.os.Bundle;

import androidx.fragment.app.Fragment;
import androidx.lifecycle.ViewModelProvider;

import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.TextView;

/**
 * A simple {@link Fragment} subclass.
 * Use the {@link FragmentB#newInstance} factory method to
 * create an instance of this fragment.
 */
public class FragmentB extends Fragment {
    private SharedViewModel sharedViewModel;
    private TextView textView;

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
        View view = inflater.inflate(R.layout.fragment_b, container, false);
        textView = view.findViewById(R.id.tvTampung);

        sharedViewModel = new ViewModelProvider(requireActivity()).get(SharedViewModel.class);
        sharedViewModel.getSelectedItem().observe(getViewLifecycleOwner(), item -> {
            textView.setText(item);
        });

        return view;
    }
    // TODO: Rename parameter arguments, choose names that match
    // the fragment initialization parameters, e.g. ARG_ITEM_NUMBER
    private static final String ARG_PARAM1 = "param1";
    private static final String ARG_PARAM2 = "param2";

    // TODO: Rename and change types of parameters
    private String mParam1;
    private String mParam2;

    public FragmentB() {
        // Required empty public constructor
    }

    /**
     * Use this factory method to create a new instance of
     * this fragment using the provided parameters.
     *
     * @param param1 Parameter 1.
     * @param param2 Parameter 2.
     * @return A new instance of fragment FragmentB.
     */
    // TODO: Rename and change types and number of parameters
    public static FragmentB newInstance(String param1, String param2) {
        FragmentB fragment = new FragmentB();
        Bundle args = new Bundle();
        args.putString(ARG_PARAM1, param1);
        args.putString(ARG_PARAM2, param2);
        fragment.setArguments(args);
        return fragment;
    }

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        if (getArguments() != null) {
            mParam1 = getArguments().getString(ARG_PARAM1);
            mParam2 = getArguments().getString(ARG_PARAM2);
        }
    }
}
```
#### MainActivity.java: MainActivity pada Android berfungsi sebagai jembatan utama antara sistem operasi dan UI aplikasi, mengelola siklus hidup aplikasi, dan menangani interaksi dengan pengguna. Activity ini juga sering bertanggung jawab untuk mengelola navigasi antar layar dan fragment. Berikut tampilan Shortcutnya:

```sh
package com.example.ppm2;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        FragmentA fragmentA = new FragmentA();
        getSupportFragmentManager().beginTransaction()
                .replace(R.id.fragment_container_a, fragmentA)
                .commit();

        FragmentB fragmentB = new FragmentB();
        getSupportFragmentManager().beginTransaction()
                .replace(R.id.fragment_container_b, fragmentB)
                .commit();
    }
}
```
### XML File
 Pada penerapan Aplikasi ini saya menggunakan 4 file XML untuk mendeskripsikan berbagai aspek dari aplikasi, terutama antarmuka pengguna (UI) dan konfigurasi. berikut file xml:
 ```sh
Activity_Main.xml
```
 ```sh
Fragment_a.xml
```
 ```sh
fragment_b.xml
```
## MOXFIX
Berikut Merupakan Tampilan Aplikasi Moxfix :

