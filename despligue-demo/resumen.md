# Tabla Git

| Comando | Función | Ejemplo |
|----------|----------|----------|
|  Init   | Inicia un repositorio   | git init   |
|  Config   | Definir valores de configuración   | git config --global|
|  Add   | Añade elemento al stage   | git add elemento.md   |
|  Commit   | Captura una instantánea de los cambios preparados en ese momento del proyecto   | git commit elemento.md -m "mensaje"   |
|  Status   | Ver el estado del directorio de trabajo   | git status   |
|  Log   | Muestra las instantáneas confirmadas   | git log --oneline   |
|  Diff   | Ver las diferencias entre commits   | git diff (commit) (commit2)   |
|  Show   |  mostrar un objeto Git de una manera simple y legible por humanos   | git show HEAD  |
|  Tag   | Sirve para etiquetar con un tag el estado del repositorio completo   | git tag v2.0 (commit)   |
|  Restore   | Restaurar algún archivo o el proyecto por completo   | git restore elemeto.md   |
|  Revert   | Deshace un commit   | git revert (commit)   |
|  Reset   | Reinicia el HEAD a un commit  | git reset (commit)   |
|  Branch   | Ver las ramas del repositorio   | git branch   |
|  Switch   | Cambia de una rama a otra   | git switch (rama)   |
|  Merge   | Fusiona las ramas   | git merge (rama)   |
|  Remote   | Ver los repositorios remotos   | git remote -v   |
|  Clone   | Clona un repositorio al directorio local   | git clone   |
|  Push   | Sube el repositorio local al remoto   | git push   |
|  Pull   | Baja el repositorio remoto a local   | git pull   |
|  Fetch   | Obtienes los cambios del repositorio remoto   | git fetch   |