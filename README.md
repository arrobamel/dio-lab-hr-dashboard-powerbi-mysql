# 🏢 Azure Company - HR and Projects Dashboard

> Projeto desenvolvido no Bootcamp da DIO - Processamento de dados com Power BI
> 

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![MySQL Workbench](https://img.shields.io/badge/MySQL%20Workbench-00758F?style=for-the-badge&logo=mysql&logoColor=white)
![Microsoft Azure](https://img.shields.io/badge/Microsoft%20Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Power Query](https://img.shields.io/badge/Power%20Query-F2C811?style=for-the-badge&logo=microsoft&logoColor=black)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)

---



### 🗄️ Modelagem do Banco - MySQL Workbench
![Diagrama](diagrama_azure_company.png)
> Diagrama relacional criado no MySQL Workbench

<img width="591" height="605" alt="diagrama_azure_company" src="https://github.com/user-attachments/assets/ff944f05-6ba3-4355-b1c2-ac29265508a0" />

**Tabelas:** `Company`, `Departments`, `Employee`, `Payroll`, `Projects`

Relacionamentos:
- `Employee.Department_ID` -> `Departments.ID`
- `Payroll.Employee_ID` -> `Employee.ID`
- `Projects.Department_ID` -> `Departments.ID`


---

### 📊 Dashboard Final
> Print do Dashboard conectado com Power Bi
> ### 📊 Dashboard Final - Power BI
![Dashboard](relatorio.png)

<img width="906" height="504" alt="relatorio" src="https://github.com/user-attachments/assets/68285dfc-3dd5-41ca-a9ca-28cbc9f1dbf5" />

*Total de 8 funcionários | Soma de Salários: R$ 281k | Distribuição por departamento*




---

### 🛠️ Como foi feito

1.  Criei o banco de dados MySQL localmente no Workbench com as tabelas `Company, Departments, Employee, Payroll e Projects`, seguindo a mesma estrutura proposta para a Azure.
2.  Conectei o Power BI Desktop direto no MySQL usando o conector nativo.
3.  Apliquei **Mesclar Consultas (Merge)** para relacionar as tabelas e criar o modelo estrela para o dashboard.
4.  Criei os visuais de RH: Total de 8 Funcionários e Soma de Salários por Departamento.

---

### 🔄 Conceito Chave: Mesclar vs Combinar Consultas


**1. O que é MESCLAR CONSULTAS (Merge Queries)?**
É um `JOIN` horizontal. Une colunas de tabelas diferentes usando uma chave em comum.
Ex: Trazer o `Nome do Departamento` para dentro da tabela `Employee`.

**2. O que é COMBINAR / ANEXAR CONSULTAS (Append Queries)?**
É um `UNION` vertical. Empilha linhas de tabelas que tem a MESMA estrutura.
Ex: Juntar `Funcionarios_Jan` + `Funcionarios_Fev`.

**3. Por que usei SÓ MESCLAR nesse projeto e NÃO Combinar?**

Porque nossas tabelas têm estruturas DIFERENTES e são relacionais. Se eu usasse Combinar, o Power BI iria empilhar salário com nome de departamento, gerando linhas nulas e duplicando os valores. Minha soma de R$ 281k ficaria errada.

Usando **Mesclar (Merge)**, eu preservei o modelo relacional:
- `Payroll` + `Employee` = sei quanto cada pessoa ganha
- `Employee` + `Departments` = sei de qual dept ela é

Resultado: Dashboard correto, sem duplicidade. Mesclar é para relacionar, Combinar é para unir tabelas iguais.

---
Feito por Melissa Machado para o desafio da DIO.
