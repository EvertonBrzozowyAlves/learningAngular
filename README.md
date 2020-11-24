# Angular

O Angular é um dos frameworks SPA (Single Page Application) mais famosos, juntamente com o React e o Vue.  
O conceito de SPA é o que, uma vez carregada a página Index, não será feito nenhum outro carregamento de tela.  
Não será feito nenhum carregamento de HTML, apenas dados trafegados via HTTP e manipulação do DOM para apresentação desse conteúdo.  

## Componentes
Componentes são como módulos que criamos, que unem o html, o css e o javascript para ser apresentado posteriormente.  
Tudo em Angular é um componente.
Os componentes ficam, por padrão, na pasta **app**.  
O arquivo app.component.ts informa qual o html, css e gerará também o javascript para esse componente:

```typescript
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  testando = 'Teste';
}
```

***Selector:*** É a 'tag' HTML a ser utilizada para retornar todo o componente.  
***templateUrl:*** É o corpo html do componente.  
***styleUrls:*** É o CSS associado ao componente.  
A export class é o código TS que será transpilado para JS, também associado ao componente.  

Os componentes podem receber atributos como parâmetro.  
Dessa forma, ao utilizar determinado componente, passamos esse atributo como parâmetro e ele é associado ao respectivo atributo da classe, sendo em seguida recuperado no arquivo HTML do componente original, utilizando a síntaxe [].  

No componente, adicionamos:
```typescript
import { Component, Input } from "@angular/core";

export class PhotoComponent {
  @Input() caminhoImagem = '';
}
```

No arquivo que irá utilizar o componente, passamos o valor para aplicar ao atributo da classe:
```html
<ap-photo caminhoImagem="https://url/para/photo.jpg" descricao="descricao"></ap-photo>
```
## Convenções  
Para arquivos usamos letras minúsculas menubar.component.ts, no nome da classe usamos MenubarComponent.  

Para preencher valores dentro de tags, utilizando propriedades da classe, usamos o Angular Expression **{{}}**.  
Dentro das chaves, adicionamos uma propriedade da classe do componente.  
Quando queremos utilizar as mesmas propriedades de classes para preencher atributos de tags, como src, alt,  
decoramos esse atributo com **[]** e como valor da propriedade passamos o nome da propriedade da classe:

**HTML:**
```html
<h1>{{testando}}</h1>
<img [src]="caminhoImagem" [alt]="descricao">

```
**Component.ts:**
```typescript
export class AppComponent {
  testando = 'Teste';
  caminhoImagem = 'https://avatars0.githubusercontent.com/u/51219903?s=400&u=780598fc27ff301d473f70fc285ccb4180cbad07&v=4';
  descricao = 'teste de imagem';
}
```

Devemos prefixar componentes com uma sigla que indique o projeto ou a empresa, mas sempre prefixe os componentes!
```HTML
<app-combo></app-combo>
```

Quando criar um componente, ele deve ser adicionado a um módulo, no arquivo app.module.ts.  
Nesse arquivo, deixe primeiro os imports próprios do Angular, depois os criados.  

## Importando arquivos globais
Para importar CSS ou Scripts globais, fazemos um processo um tanto diferente do convencional.  
Devemos instalar a biblioteca pelo npm (de preferência) e indicar o caminho na pasta node_modules dessa dependência no arquivo de configuração angular.json.  
**npm install**
```bash
npm install bootstrap
```

**angular.json**
```json
"styles": [
  "src/styles.css",
  "./node_modules/bootstrap/dist/css/bootstrap.min.css"
],

```
