---
max_turns: 8
allowed_tools: [Read, Glob, Grep, Skill]
---

Tengo un bug en mi app Laravel: un paciente logueado puede ver las citas de otro paciente cambiando el número en la URL /citas/15. Este es el controlador. Dame la corrección.

```php
class CitaController extends Controller
{
    public function show($id)
    {
        $cita = Cita::findOrFail($id);
        return view('citas.show', compact('cita'));
    }
}
```
