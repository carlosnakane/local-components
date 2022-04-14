# Consumindo Pacotes Locais

> Esse é um exemplo de como consumir pacotes locais.

## Motivaçao
Algumas ferramentas de análise de qualidade como por exemplo o SonarQube apontam como problema o import de módulos que não estão definidos como dependência no package.json.

Exemplo:
```
import Modal from 'components/modal'
```

Esse tipo de import pode ocorrer quando temos por exemplo uma biblioteca de componentes do próprio projeto e por questões de simplicidade não desejamos publica-la em um registry.

## Solução
Existem várias formas de contornar isso e uma delas é instalar a sua biblioteca local com o ``file:`` no package.json.

Para isso:
1. Crie um arquivo ``package.json`` na raiz da sua biblioteca. Coloque algo significativo na propriedade name dele. Ex: my-awesome-components;
2. Adicione como dependência no package.json da aplicação da seguinte forma: ``"my-awesome-components": "file:./src/my-awesome-components"``.
3. Rode ``npm install`` na sua aplicação.
4. Agora é só importar o modulo como um pacote normal: ``import CompB from 'my-awesome-components/comp-b';``

Veja os arquivos ``src/package.json``, ``src/my-awesomne-components/package.json`` e ``src/App.tsx`` pra mais detalhes.