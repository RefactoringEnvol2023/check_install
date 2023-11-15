# Prérequis pour le cours Refactoring d'Envol 2023

## Checklist

### Git (**obligatoire**)

* Installer [git](https://code-club.io.ias.u-psud.fr//docs/install/install-git.html)

### Python

* Installer python en version 3.10
  * [avec pyenv (**recommandé**)](https://code-club.io.ias.u-psud.fr//docs/install/install-python.html#installation)
  * ou directement selon votre plateforme
    * [Windows](https://docs.python.org/fr/3/using/windows.html)
    * [MacOs](https://www.python.org/downloads/macos/)
    * [Linux](https://docs.python.org/fr/3/using/unix.html)
* S'assurer que vous pouver [créer un environnement virtuel](https://code-club.io.ias.u-psud.fr//docs/install/install-virtualenv.html)
  * Si vous avez des difficultés sous debian, installer `sudo apt-get install python3-venv`
* Installer les libraries suivant avec `pip`
```
python -m pip install -U pip
python -m pip install pytest pytest-sugar coverage
```  
 
### Pycharm

* Installer la version Community de Pycharm [(voir guide)](https://code-club.io.ias.u-psud.fr//docs/install/ide.html#pycharm)
 
### Docker

* Installer [docker](https://docs.docker.com/engine/install/) et s'assurer que vous pouvez lancer `docker run hello-world`
* Faire `docker pull sonarqube`
* Faire `docker pull sonarsource/sonar-scanner-cli`

### Test de validation de l'installation python

Nous allons créer un projet factice

* Ouvrir un terminal 
* Créer le projet
```  
     mkdir MyProject
     cd MyProject
```

Les commandes de base que vous utiliserez sont les suivantes :

#### Créer l'environnement

```
    python -m venv .venv --prompt MyProject
```
    

#### Activer l'environnement

**(Linux/MacOs)**

```
source .venv/bin/activate
```

une version raccourcie consiste à utiliser un point `.`
```
. .venv/bin/activate
```

**Windows**

Activation
```
.venv/Script/Active.ps1
```
Désactivation
```
deactivate
```
Si vous utilisez powershell pour exécuter virtualenv, vous pouvez avoir un problème de `Set-ExecutionPolicy` lors de l'activation.
Si cela se produit, exécutez cette commande avant

```powershell
Set-ExecutionPolicy Unrestricted -Scope Process
```

**Pour désactiver l'environnement :.**

```
deactivate
```

#### Validation

* Activer l'environnement dans MyProject (cf. ci-dessus)
* Installer des dépendances

```
pip install -U pip
pip install pytest pytest-sugar coverage
```
* Créer un fichier `./my_module.py` à la racine du projet
```
def fn(a, b):
  return f'{a}:{b}'
```
* Créer un fichier `./pytest.ini` dans le même répertoire
```ini
[pytest]
pythonpath = .
testpaths = tests
```
* Créer un répertoire `./tests`
* Créer un fichier `./tests/test_my_module.py`
```python
from my_module import fn
def test_fn():
    #__given__
    a=1
    b='bar'

    #__when__    
    result = fn(a, b)

    #__then__
    assert result == '1:bar'
```
* Lancer dans le terminal la commande
```
pytest
```

Vous devez avoir quelque chose qui ressemble à 

```
Test session starts (platform: win32, Python 3.10.0, pytest 7.4.2, pytest-sugar 0.9.7)
rootdir: C:\Workdir\check
configfile: pytest.ini
testpaths: tests
plugins: sugar-0.9.7
collected 1 item

 tests/test_my_module.py ✓                                                                                                                                                                                                                                                                                                                                                     100% ██████████
Results (0.04s):
       1 passed
```

  



