Para eliminar el archivo pesado de git se utilizaron los siguientes comandos:

1. Para poder recorrer todos los commits y eliminar la referencia que se encontraba en el trackeo de Git.
	git filter-branch --index-filter 'git rm -r --cached --ignore-unmatch sc.16.tar.gz' HEAD

2.Luego se eliminaron las nuevas referencias creadas por el comando filter-branch y las que se mantienen en git reflog.
	rm -Rf .git/refs/original
	rm -Rf .git/logs/

3.Luego se optimiza el repositorio eliminando archivos innecesarios.Con esto ya no se considerará al pushear.
	git gc

4.Para poder eliminarlo por completo se ejecuto el siguiente comando.
	git prune --expire now