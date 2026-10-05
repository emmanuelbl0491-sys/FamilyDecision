# privado/ — Zona ROJA y ÁMBAR (solo en tu computadora)

Esta carpeta **nunca** se sube a Claude, a GitHub ni a ningún servicio en la nube. `.gitignore` la bloquea.

## Qué va aquí
| Archivo sugerido | Zona | Contenido |
|---|---|---|
| `clave-alias.md` | ROJA | Relación alias ↔ nombre real |
| `datos-familia.xlsx` | ÁMBAR | Cifras exactas: ingresos, saldos, edades |
| `documentos/` | ROJA | Identificaciones, pólizas, expedientes (mejor en un gestor de contraseñas cifrado) |

## Plantilla: clave de alias
```markdown
| Alias   | Nombre real | Notas |
|---------|-------------|-------|
| Padre-A |             |       |
| Padre-B |             |       |
| Hijo-1  |             |       |
```

## Ejemplo (EJEMPLO FICTICIO)
```markdown
| Alias   | Nombre real | Notas            |
|---------|-------------|------------------|
| Padre-A | (nombre)    | Arquitecto IA    |
| Hijo-1  | (nombre)    | Nacido en 2022   |
```

## Regla de salida
Un dato sale de esta carpeta solo convertido en **banda o alias**. Ejemplo: "ingreso 74,300 USD/año" sale como "Banda C (60–80k USD/año)".
