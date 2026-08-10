# Guía de uso del repositorio — Equipo Hackless

## 1. Estructura inicial 

```
/
├── README.md
├── GUIA_USO_REPOSITORIO.md
├── .gitignore
├── src/
├── docs/
└── .github/
    ├── ISSUE_TEMPLATE/
    └── PULL_REQUEST_TEMPLATE.md
```

---

## 2. Roles y permisos del equipo

| Rol | Quién | Permisos |
|---|---|---|
| Admin | Vos / líder técnico | Puede cambiar settings, borrar el repo, gestionar colaboradores |
| Maintain | Referentes técnicos | Puede mergear PRs, gestionar issues, no puede borrar el repo |
| Write | Resto del equipo (desarrolladores) | Puede crear ramas, subir commits, abrir PRs |
| Read | Invitados externos / stakeholders (si aplica) | Solo lectura |

---

## 3. Flujo de trabajo (workflow) — paso a paso para el equipo

1. **Clonar el repositorio** (una sola vez):
   ```
   git clone https://github.com/usuario/repo.git
   ```
2. **Actualizar `main` antes de empezar** cualquier tarea:
   ```
   git checkout main
   git pull origin main
   ```
3. **Crear una rama nueva** para cada tarea/feature (nunca trabajar directo sobre `main`):
   ```
   git checkout -b feature/nombre-tarea
   ```
4. **Hacer commits chicos y descriptivos**:
   ```
   git add .
   git commit -m "feat: agrega validación de formulario de login"
   ```
5. **Subir la rama**:
   ```
   git push origin feature/nombre-tarea
   ```
6. **Abrir un Pull Request (PR)** hacia `main`, describiendo qué se hizo y por qué.
7. **Esperar al menos 1 revisión (code review)** de otro miembro del equipo antes de mergear.
8. **Mergear** solo cuando el PR esté aprobado y sin conflictos.
9. **Borrar la rama** una vez mergeada, para mantener el repo limpio.

---

## 4. Qué SÍ se puede hacer

- Crear ramas propias para cada tarea.
- Abrir issues para reportar bugs, proponer mejoras o pedir ayuda.
- Comentar y revisar Pull Requests de compañeros.
- Usar Discussions (si se habilita) para dudas técnicas del equipo.
- Documentar decisiones técnicas en `/docs`.
- Actualizar el README cuando se agregan funcionalidades nuevas.

## 5. Qué NO se puede hacer

- **No subir credenciales, tokens, claves API ni datos de clientes** — el repo es público, todo lo que se sube queda visible para cualquiera.
- **No hacer push directo a `main`** (la rama debe estar protegida).
- **No hacer force push** (`git push --force`) sobre ramas compartidas.
- **No mergear PRs propios sin revisión** de al menos otro integrante.
- **No borrar ramas o el repositorio** sin autorización del admin.
- **No subir archivos pesados** (binarios, videos, datasets grandes) — usar Git LFS o almacenamiento externo si es necesario.
- **No compartir información interna/confidencial de Hackless o de clientes** en issues, commits o PRs, ya que el repo es público.

---

## 6. Configuración recomendada de protección de rama (`main`)

En **Settings → Branches → Add rule**:
- Require a pull request before merging: 
- Require approvals: mínimo 1
- Require status checks to pass (si hay CI configurado): 
- Do not allow force pushes: 
- Do not allow deletions: 

---

## 7. Convención de nombres de rama

- `feature/nombre-descriptivo` → nueva funcionalidad
- `fix/nombre-descriptivo` → corrección de bug
- `docs/nombre-descriptivo` → cambios de documentación
- `hotfix/nombre-descriptivo` → arreglo urgente sobre producción

---

## 8. Convención de commits (sugerida)

Formato: `tipo: descripción breve`

- `feat:` nueva funcionalidad
- `fix:` corrección de bug
- `docs:` documentación
- `refactor:` cambios internos sin alterar funcionalidad
- `test:` agregado o ajuste de tests
- `chore:` tareas de mantenimiento (configuración, dependencias, etc.)