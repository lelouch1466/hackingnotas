
## Reto
Rust fixme 3
## Descripcion
Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag!Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/dcdaf491b35c1d0f5075e9583edbbb7aaea1dffb6ad32bc000e4d87b5200ff7b/fixme3.tar.gz).

## Solucion
- descargo el archivo y trato de armarlo con `cargo build` y me da este error
```
  --> src/main.rs:31:31
   |
31 |         let decrypted_slice = std::slice::from_raw_parts(decrypted_ptr, decrypted_len);
   |                               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ call to unsafe function
   |
   = note: consult the function's documentation for information on how to avoid undefined behavior

For more information about this error, try `rustc --explain E0133`.
error: could not compile `rust_proj` (bin "rust_proj") due to 1 previous error

```

- le pregunte a chatgpt como se arregla esa linea y me dio esta para reemplazar
```
let decrypted_slice = &decrypted_buffer[..];
```
- la reemplazo en el src y ahora trato de compilarlo
- me salen mas mensajes pero no creo que sean de error
- trato de correrlo con `cargo run` y me dal la bandera: **picoCTF{n0w_y0uv3_f1x3d_1h3m_411}
**

## Notas
-Sigo sin entender en lo mas minimo rust (manita arriba)

## Referencias
