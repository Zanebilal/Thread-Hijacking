#  Thread Hijacking Techniques

This repo showcases how to hijack threads in both local and remote processes to execute arbitrary code (like shellcode) without creating new threads. These techniques are useful in malware, red teaming, and EDR bypass scenarios when you want stealthier execution.

> 🔬 For research and educational use only. Don't be dumb with this.

## 📖 What’s Inside?

This repo includes working implementations of two thread hijacking techniques:

- **Local Thread Hijacking**
  - Suspend your own thread.
  - Modify the context to point to your shellcode.
  - Resume and execute.

- **Remote Thread Hijacking**
  - Open a target process and thread.
  - Suspend the thread, overwrite the instruction pointer with a payload.
  - Resume the thread and boom — code exec in the remote process.

No `CreateRemoteThread`. No `NtCreateThreadEx`. Just good old thread manipulation using `SetThreadContext`.

---

## 🧰 Techniques

### 🔧 Local Thread Hijacking

Basic idea:
1. Get a handle to your own thread.
2. Suspend it.
3. Change the instruction pointer (EIP/RIP) to point to shellcode.
4. Resume and execute.


### 🌐 Remote Thread Hijacking

Basic idea:
1. Open the remote process after creating it in suspend state.
2. Inject shellcode into the remote process.
3. Resume the susoended thread

 
## Getting Started
1. Clone the repository:

```bash
    git clone https://github.com/Zanebilal/Thread-Hijacking
```
2.  Navigate to the desired technique folder and compile: 

```bash
    cd Thread Hijacking/localThreadHijacking/localThreadHijacking
    gcc main.c -o main
 ```

## 📚 Further Reading

Want to dive deeper? Here are some great resources:

- [microsoft docs](https://learn.microsoft.com/en-us/windows/win32/api/processthreadsapi/nf-processthreadsapi-getthreadcontext)
- [Malware Development for Ethical Hackers book](https://www.abebooks.co.uk/9781801810173/Malware-Development-Ethical-Hackers-Learn-1801810176/plp)
