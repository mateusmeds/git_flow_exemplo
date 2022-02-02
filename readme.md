# Projeto de exemplo gitflow

## Branches

### **Master**
É a Branch que controla o sistema que está em produção.

### **Develop**
É a Branch base para desenvolver novos recursos e, posteriormente, integrar esses recursos na Branch Master.

### **Features**
É uma branch que é criada para desenvolver cada nova funcionalidade. Usa como base a Branch Develop e, após finalizar a implementação, faz um ```merge``` com a Branch Develop.

#### Antes de finalizar a Feature é necessário  publicar as alterações para o repositório remoto

```
git push origin nome_da_feature
```

#### Criando uma Feature
```
git flow feature start nome_da_feature
```
#### Finalizando a Feature criada
#### Com um único comando faz o merge com a Branch Develop, exclui a Branch de Feature e faz o checkout para a Branch Develop
```
git flow feature finish nome_da_feature
```

#### agora tem que publicar as alterações da Branch Develop para o repositório remoto

```
git push origin develop 
```

### **Release**
É a Branch que controla a versão do projeto. Quando desenvolver um determinado conjunto de Features/implementações necessários para lançar uma nova versão do sistema. Após a aprovação do Release, faz um ```merge``` com a Branch Master e a Develop para manter a base de desenvolvimento atualizada.

#### Criando um Release
```
git flow release start versao_da_release
```

#### Publicando o Release
```
git flow release publish versao_da_release
```

#### Finalizando o Release
#### Com este comando faz o merge para as branches Master e Develop, deleta a Release criada e faz o checkout para a Develop.
```
git flow release finish -m "Mensagem de merge" versao_da_release
```

#### Publicando as Branches Master e Develop
```
git push origin develop && git push origin master
```

### **Hotfixes**
É a Branch responsável por fazer correções de erros que ocorrem em produção. Essa branch surge como uma necessidade de corrigir erros imediatos sem precisar passar por todo o fluxo de desenvolvimento novamente. Uma vez corrigidos os erros, faz um merge com a Branch Master e a Develop.