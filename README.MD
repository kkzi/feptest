
# FEP �ļ�����Э�� (File Exchange Protocol) 

ĳ�����ڴ����ļ���Э��ʵ�֣���ʵ�֣�
- UDP����
- UDP����
- TCP����
- TCP����


### ���ն�

```cpp
auto recv = make_fep_server(fep_protocol::TCP);
recv->set_local_host({ "127.0.0.1", 28001 });
recv->run([](auto &&progress) {
    std::cout << "received file: " << progress.filename << " progress: " << progress.progress << std::endl;
});
```



### ���Ͷ�

```cpp
auto sender = make_fep_client(fep_protocol::TCP);
sender->set_local_host({ "127.0.0.1", 29001 });
sender->set_remote_host({ "127.0.0.1", 28001 });
sender->send("somefile.zip", [](auto &&progress) {
    std::cout << "send " << progress.filename << " progress: " << progress.progress << std::endl;
});
```


