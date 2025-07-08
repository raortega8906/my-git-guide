# 🚀 Guía Básica de Git para Proyectos Individuales

Esta guía está diseñada para ayudarte a trabajar con Git de forma ordenada y profesional, incluso si estás solo en el proyecto. Te servirá como base para mejorar tu flujo de trabajo y prepararte para trabajar en equipo más adelante. (Principiantes).

---

## 🌲 Flujo de ramas simplificado

Usamos solo dos ramas:

| Rama       | Propósito                                      |
|------------|-----------------------------------------------|
| `main`     | Rama estable, lista para producción            |
| `feature/*`| Rama temporal por cada nueva funcionalidad     |

---

## 🏷️ Convención de nombres de ramas

Cada rama describe qué hace de forma clara:

```
feature/login-jwt
feature/post-crud
feature/env-setup
```

---

## ✍️ Convención de commits

Formato:
```
[tipo]: mensaje en imperativo
```

Tipos comunes:
- `feat:` Nueva funcionalidad
- `fix:` Corrección de bug
- `refactor:` Mejora interna (sin cambio de funcionalidad)
- `style:` Formato o visual (espacios, estilos, etc)
- `docs:` Documentación
- `chore:` Tareas menores (config, dependencias)

Ejemplos:
```
feat: crear sistema de login con JWT
fix: corregir validación al guardar post vacío
refactor: mover lógica de auth a servicio
docs: actualizar sección de rutas API
chore: agregar .env al gitignore
```

---

## 🔄 Flujo de trabajo (paso a paso)

### 1. Crear una nueva funcionalidad

```bash
git checkout main
git pull origin main
git checkout -b feature/post-crud
```

Trabaja con commits frecuentes y claros:

```bash
git add .
git commit -m "feat: crear CRUD básico para posts"
git push origin feature/post-crud
```

#### 1.1. Hacer merge:

```bash
git checkout main
git pull origin main
git merge feature/post-crud
git push origin main
```

### 2. Revisar tus cambios (auto pull request)

Puedes hacer una revisión **aunque estés solo**. Así entrenas el ojo crítico.

#### 🔍 ¿Cómo hacerlo?

1. En GitHub, abre un Pull Request de `feature/post-crud` a `main`.
2. Revisa:
   - ¿Los commits tienen mensajes claros?
   - ¿Faltó borrar algún archivo de prueba?
   - ¿Se subió algo que no debe ir (`.env`, `.DS_Store`, etc)?
   - ¿El código está limpio y funcional?
3. Si ves algo raro, corrígelo en la misma rama:

```bash
git add .
git commit -m "fix: eliminar archivo innecesario"
git push
```

4. Una vez todo esté bien, haz el merge del PR en GitHub.

---

### 3. Volver a `main` y borrar rama

```bash
git checkout main
git pull origin main
git branch -d feature/post-crud
git push origin --delete feature/post-crud
```

---

## 🧼 ¿Qué hago si subo algo mal?

### 🔁 Opción 1: Arreglar con un nuevo commit

```bash
# Corriges el error
git add .
git commit -m "fix: eliminar archivo innecesario"
git push
```

### ⏪ Opción 2: Rehacer el último commit (solo si NO hiciste push)

```bash
git reset --soft HEAD~1
# vuelves a hacer el commit bien
git add .
git commit -m "feat: mensaje correcto"
```

### 🔙 Opción 3: Revertir después del push

```bash
git revert HEAD
git push
```

Esto genera un nuevo commit que deshace el anterior.

---

## 🛑 .gitignore para Laravel

Archivo `.gitignore` mínimo recomendado:

```
/vendor
/node_modules
.env
.phpunit.result.cache
/storage/*.key
/public/storage
/.vscode
.idea
.DS_Store
```

---

## ✅ Checklist de auto revisión antes de hacer merge

- [ ] ¿Los mensajes de commit son claros?
- [ ] ¿No subí `.env`, `/vendor` u otros archivos innecesarios?
- [ ] ¿Probé localmente que funciona?
- [ ] ¿Hay comentarios o código temporal por limpiar?
- [ ] ¿Los cambios están bien organizados?

---

## 📝 ¿Dónde usar esto?

Guarda este archivo como `GIT_GUIDE.md` o `CONTRIBUTING.md` en tu proyecto.

---

## 💡 Consejo final

Aunque estés trabajando solo, sigue esta guía como si fueras parte de un equipo. Así aprenderás buenas prácticas desde el inicio y tendrás proyectos más limpios, mantenibles y profesionales.
