---
max_turns: 8
allowed_tools: [Read, Glob, Grep, Skill]
---

Audita la seguridad de este archivo de mi sistema antes de subirlo a producción y dime qué corregir:

```php
<?php
// citas.php
session_start();
$conn = mysqli_connect("localhost", "root", "Admin2024!", "clinica");
ini_set('display_errors', 1);

if ($_GET['accion'] == 'ver') {
    $id = $_GET['id'];
    $res = mysqli_query($conn, "SELECT * FROM citas WHERE id = $id");
    $cita = mysqli_fetch_assoc($res);
    echo "<h2>Cita de " . $cita['paciente_nombre'] . "</h2>";
    echo "<p>Notas: " . $cita['notas_medicas'] . "</p>";
}

if ($_POST['accion'] == 'login') {
    $u = $_POST['usuario'];
    $p = md5($_POST['clave']);
    $r = mysqli_query($conn, "SELECT * FROM usuarios WHERE usuario='$u' AND clave='$p'");
    if (mysqli_num_rows($r) > 0) {
        $_SESSION['usuario'] = $u;
        error_log("Login OK usuario=$u clave=" . $_POST['clave']);
    }
}
```
