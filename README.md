# prmToolkit.Mapper
Suporte em trabalhar e converter datareader ou datatable em List no C#.

### Installation - prmToolkit.Mapper

Para instalar, abra o prompt de comando Package Manager Console do seu Visual Studio e digite o comando abaixo:

Para adicionar somente a referencia da dll
```sh
Install-Package prmToolkit.Mapper
```

### Como usar

**Linha para o objeto**  
```Mapper.FillObject<T>( dataReader );```  

**Coluna para objeto**  
```Mapper.FillObject<T>( object );```  
*Útil se você retornar apenas um único valor (por exemplo, Id) da consulta*  

**Várias linhas para List\<T\>**  
```Mapper.FillCollection<T>( dataReader );```  

**Várias linhas para List\<T\> com retorno de chamada em cada objeto**  
```Mapper.FillCollection<T>( dataReader, (T) => { //Execute alguma ação aqui });```  

**Única linha para objeto com retorno de chamada**  
```Mapper.FillObject<T>( dataReader, (T) => { //Execute alguma ação aqui });```

**Única linha para o objeto existente**  
```Mapper.FillObject<T>( dataReader, existingObject, overwriteExstingProperties);```

**Única linha para o objeto existente com retorno de chamada**  
```Mapper.FillObject<T>( dataReader, existingObject, overwriteExstingProperties, (existingObject) => { //Execute alguma ação aqui });```

### Tests

| Objetos                              | Média  | Mínimo      | Máximo      | Repetições |
|--------------------------------------------|----------|----------|----------|---------------|
| 1 novo item                                 | 0.004ms  | 0.004ms  | 0.02ms   | 500           |
| 500 novos items                              | 1.90ms   | 1.72ms   | 5.50ms   | 500           |
| 5000 novos items                             | 19.70ms  | 17.83ms  | 23.85ms  | 250           |
| 50000 novos items                            | 209.56ms | 200.54ms | 226.01ms | 100           |
| 1 novo item com Callback (chamada de retorno)           | 0.005ms  | 0.004ms  | 0.02ms   | 500           |
| 1 item existente                            | 0.004ms  | 0.0039ms | 0.02ms   | 500           |
| 1 item existente com Callback (chamada de retorno)              | 0.004ms  | 0.0039ms | 0.03ms   | 500           |
| 1 item existente sem sobrescrever propriedade | 0.007ms  | 0.006ms  | 0.03ms   | 500           |
