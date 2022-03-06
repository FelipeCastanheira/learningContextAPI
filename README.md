# 3 Passos Para Configurar Sua Aplicação Com ContextAPI

Você não aguenta mais passar estados como props de um componente para outro? Ou está fazendo a transição do Redux para o Context e não sabe por onde começar? Então este resumo é para você! 

## Passo 1 - Criar seu Context
Em uma nova pasta, você terá dois arquivos: um para o context e outro para o provider. No context, a estrutura é a seguinte:

```
import { createContext } from 'react';

const ContextName = createContext();

export default ContextName;
```

O nome do contexto é escolha sua, mas lembre-se de começar com letra maiúscula, a mesma regra serve para o Provider.

## Passo 2 - Configurar o Provider
O Provider pode ser criado como um componente funcional, na seguinte estrutura:

```
function WordProvider({ children }) {
  return (
    <ContextName.Provider value={ data }>
      { children }
    </ContextName.Provider>
  );
}
```

É preciso importar o React, o Context que você criou no passo anterior, além de useState e talvez o useEffect.

useState servirá para você criar os estados da sua aplicação, da seguinte forma:

```
const [data, setData] = useState('');
```

Sendo "data" o nome de um estado e "setData" a função que o altera. _Lembrando que isso é apenas um exemplo e você poderia criar vários estados em vez de apenas um._

O useEffect será necessário, por exemplo, caso você utilize alguma função assíncrona para estabelecer o valor do estado.

## Passo 3 - Definir o escopo do Provider;
Para aplicações pequenas, é comum aplicar o Provider como elemento-pai de todos os componentes, sendo assim, seu App.js ficará da seguinte forma:

```
function App() {
  return (
    <ProviderName>
        <Component1 />
        <Component2 />
        <Component3 />
    </ProviderName>
  );
}
```

Pronto, agora todos os componentes têm acesso ao seu estado, basta importá-lo onde quiser usá-lo com:
const data = useContext(ContextName);

Para você observar na prática, recomendo uma simples aplicação na qual estou trabalhando: [Termo's Clone](https://github.com/FelipeCastanheira/termos-clone).
