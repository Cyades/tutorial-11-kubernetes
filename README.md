# Kubernetes Tutorial
**Nama:**   Malvin Scafi<br>
**NPM:**    2306152430<br>
**Kelas:**  AdPro A<br>

## Modul 11
### Reflection on Hello Minikube
1. **Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app?**
- Sebelum ter-expose *service* : 
![](Before.png)
- Setelah ter-expose *service* : 
![](After.png)
- Benar, jumlah log mengalami peningkatan setiap kali aplikasi diakses. Hal ini terjadi karena setiap permintaan HTTP yang masuk akan menghasilkan entri log baru yang terakumulasi berdasarkan frekuensi akses aplikasi. Sebelum pod di-expose sebagai service, tidak ada log yang tercatat karena pod tersebut masih terisolasi di dalam cluster dan tidak dapat dijangkau dari luar. Setelah pod ter-expose melalui service, barulah aplikasi dapat menerima traffic dari client eksternal, sehingga mulai muncul log aktivitas.

2. **Notice that there are two versions of `kubectl get` invocation during this tutorial section. The first does not have any option, while the latter has `-n` option with value set to `kube-system`. What is the purpose of the `-n` option and why did the output not list the pods/services that you explicitly created?**
- Opsi `-n` dalam perintah `kubectl get` berfungsi untuk menentukan namespace Kubernetes yang spesifik. Namespace adalah cara untuk mengelompokkan resources dalam cluster. Ketika `kubectl get` dijalankan tanpa `-n`, secara default akan menampilkan resources dari namespace `default`. Sebaliknya, `-n kube-system` menampilkan resources di namespace `kube-system` yang berisi komponen sistem Kubernetes seperti kube-proxy, coredns, dan control plane.
- Pods dan services yang dibuat berada di namespace `default`, sementara `kubectl get -n kube-system` hanya menampilkan resources di namespace `kube-system`. Kedua perintah melihat "ruang" yang berbeda dalam cluster yang sama, sehingga menghasilkan output yang berbeda sesuai isi masing-masing namespace.