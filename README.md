   
# JoaoDalonso-FATEC_DES_WEB2_2025_Avaliacao2
![image](https://github.com/user-attachments/assets/35d91f42-0648-4305-938e-e8ae72d39eed)  
DIAGRAMA DE CASO DE USO DA PROVA - >





 ![image](https://github.com/user-attachments/assets/d3725470-1b31-40ee-aecb-f16d999c9f55)








1- CLASSE CADASTRO(CLASS_BANCO).   
2- CADASTRAR PRODUTOS.
3- REMOVER PRODUTO.                                                                                                                                    
4- LISTAR PRODUTOS.
5- READ ME.                                                                                                                                                     

                                                                                                                                                       
                                                                                                      
INSTALAÇÃO:

Clone o repositório:
git clone "https://github.com/JoaoDalonso/JoaoDalonso-FATEC_DES_WEB2_2025_Avaliacao2"


Acesse a pasta do projeto:
cd PROVA_ORLANDO

Configure o banco de dados em class_banco.php:
private $host = 'localhost';
private $db   = 'nome_do_banco'; <- artesanato_db
private $user = 'usuario'; <- root
private $pass = 'senha'; <- ***********


Crie a tabela produtos (exemplo MySQL):

CREATE TABLE produtos (
  id INT AUTO_INCREMENT PRIMARY KEY,                                                                                                                       
  nome VARCHAR(100) NOT NULL,
  preco DECIMAL(10,2) NOT NULL,
  descricao VARCHAR(255) NOT NULL,
  categoria VARCHAR(30) NOT NULL
);
                                                                     

Coloque todos os arquivos no diretório do servidor web (ex: htdocs/PROVA_ORLANDO).

![image](https://github.com/user-attachments/assets/206b46db-ccf3-4b2f-b76e-4b3628b85e8a)
![image](https://github.com/user-attachments/assets/122be105-b2ad-4eae-8862-77ff1abe05c9)
![image](https://github.com/user-attachments/assets/e70f8030-8605-4a8c-be1a-f89a664e955f)
![image](https://github.com/user-attachments/assets/931575ac-4dd6-4c5e-a56b-aa8ee2110437)
![image](https://github.com/user-attachments/assets/abe2dcfa-8277-451b-8014-fe7ed49b1327)

CADA QUERY -> (INSERIR DADOS) -> public function addProduct($nome,$preco,$descricao,$categoria){
        $sql="INSERT INTO produtos_artesanais(nome_produto,preco,descricao,categoria)VALUES(:nome,:preco,:descricao,:categoria)";
        $stmt=$this->pdo->prepare($sql);
        $stmt->execute([':nome'=>$nome,':preco'=>$preco,':descricao'=>$descricao,':categoria'=>$categoria]);
    } //Função addProduct (função que irei chamar para criar o php referente ao cadastro), $sql="INSERT INTO" usando comando sql no PHP, chamando a tabela e colocando em ordem a ser inserida na tabela os itens, e a penultima linha "$stmt = $this->pdo->prepare($sql);" declara this ->PDO, usando o método prepare() para evitar mais de uma query igual ao mesmo tempo.//

(REMOVER DADOS) ->  public function removeProduct($id){
        $sql="DELETE FROM produtos_artesanais WHERE id=:id";
        $stmt=$this->pdo->prepare($sql);
        $stmt->execute([':id'=>$id]);      // A lógica segue a mesma a diferença é o criterio de seleção, que nesse caso é o id, onde é criada uma variável para o ID onde o item selecionado pelo usuário é excluido com base no id aonde o valor do "placeholder"(aquele que é exibido ao usuário para exemplificar algo) é dado ao valor de id da variável. //
    }

(LISTAR ITENS ) - > public function getAllProducts(){
        $stmt=$this->pdo->query("SELECT * FROM produtos_artesanais ORDER BY id");
        return $stmt->fetchAll(PDO::FETCH_ASSOC);
    }  //É feito um select simples aonde é feito um comando sql completo de procura na query do codigo, usando fetchall para chamar todas as linhas e usando PDO::FETCH_ASSOC para retornar cada linha como um array para facilitar na hora de ser printado para o usuário.//



CONSIDERAÇÕES FINAIS, foi um projeto muito divertido de ser feito, aonde coloquei em prática diversas coisas aprendidas nas aulas, encapsulamentos(Aprendido em PHP/JAVA), orientação a objeto(JAVA), chamar as funções(1*SEM lógica), construct e destruct(JAVA/PHP) e inclusive exibir produtos e fazer esse foreach aprendi com o Nilton(BD).
















    
    


