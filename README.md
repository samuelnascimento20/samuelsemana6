# samuelsemana6


### Diagrama Entidade-Relacionamento

<div align="center">
  <sub>Figura X - Diagrama Entidade-Relacionamento Contábil</sub><br><br>
  <img src="https://res.cloudinary.com/davpvmkhd/image/upload/v1726459075/Captura_de_tela_2024-09-16_004949_gcjo4e_qmjy3z.png" />
  <br><br><sup>Fonte:Autores</sup>
</div> 


### Código SQL

CREATE TABLE Itens (
    ID_Item INT PRIMARY KEY,
    Descricao VARCHAR(255)
);

CREATE TABLE OCRD (
    ID_OCRD INT PRIMARY KEY,
    Detalhes VARCHAR(255)
);

CREATE TABLE Cliente (
    ID_Cliente INT PRIMARY KEY,
    Nome VARCHAR(255)
);

CREATE TABLE Compra (
    ID_Compra INT PRIMARY KEY,
    ID_Cliente INT,
    Data DATE,
    Valor DECIMAL(10, 2),
    FOREIGN KEY (ID_Cliente) REFERENCES Cliente(ID_Cliente)
);

CREATE TABLE RelatoriosFinanceiros (
    ID_Relatorio INT PRIMARY KEY,
    Titulo VARCHAR(255),
    Data DATE
);

CREATE TABLE CRD1 (
    ID_CRD1 INT PRIMARY KEY,
    Detalhes VARCHAR(255)
);

CREATE TABLE CRD7 (
    ID_CRD7 INT PRIMARY KEY,
    Informacao VARCHAR(255)
);

-- Relacionamentos
-- Possui
CREATE TABLE Possui (
    ID_Item INT,
    ID_OCRD INT,
    FOREIGN KEY (ID_Item) REFERENCES Itens(ID_Item),
    FOREIGN KEY (ID_OCRD) REFERENCES OCRD(ID_OCRD)
);

-- Emite
CREATE TABLE Emite (
    ID_Cliente INT,
    ID_Compra INT,
    FOREIGN KEY (ID_Cliente) REFERENCES Cliente(ID_Cliente),
    FOREIGN KEY (ID_Compra) REFERENCES Compra(ID_Compra)
);

-- Fornece
CREATE TABLE Fornece (
    ID_Relatorio INT,
    ID_CRD1 INT,
    FOREIGN KEY (ID_Relatorio) REFERENCES RelatoriosFinanceiros(ID_Relatorio),
    FOREIGN KEY (ID_CRD1) REFERENCES CRD1(ID_CRD1)
);

-- Registra
CREATE TABLE Registra (
    ID_Relatorio INT,
    ID_CRD7 INT,
    FOREIGN KEY (ID_Relatorio) REFERENCES RelatoriosFinanceiros(ID_Relatorio),
    FOREIGN KEY (ID_CRD7) REFERENCES CRD7(ID_CRD7)
);


### Còdigo XML

<?xml version="1.0"?>
<DatabaseSchema>
    <Tables>
        <Table name="Itens">
            <Column name="ID_Item" type="INT" primaryKey="true"/>
            <Column name="Descricao" type="VARCHAR" length="255"/>
        </Table>
        <Table name="OCRD">
            <Column name="ID_OCRD" type="INT" primaryKey="true"/>
            <Column name="Detalhes" type="VARCHAR" length="255"/>
        </Table>
        <Table name="Cliente">
            <Column name="ID_Cliente" type="INT" primaryKey="true"/>
            <Column name="Nome" type="VARCHAR" length="255"/>
        </Table>
        <Table name="Compra">
            <Column name="ID_Compra" type="INT" primaryKey="true"/>
            <Column name="ID_Cliente" type="INT"/>
            <Column name="Data" type="DATE"/>
            <Column name="Valor" type="DECIMAL" precision="10" scale="2"/>
        </Table>
        <Table name="RelatoriosFinanceiros">
            <Column name="ID_Relatorio" type="INT" primaryKey="true"/>
            <Column name="Titulo" type="VARCHAR" length="255"/>
            <Column name="Data" type="DATE"/>
        </Table>
        <Table name="CRD1">
            <Column name="ID_CRD1" type="INT" primaryKey="true"/>
            <Column name="Detalhes" type="VARCHAR" length="255"/>
        </Table>
        <Table name="CRD7">
            <Column name="ID_CRD7" type="INT" primaryKey="true"/>
            <Column name="Informacao" type="VARCHAR" length="255"/>
        </Table>
        <!-- Relacionamentos podem ser representados como tabelas de junção ou atributos foreign key -->
    </Tables>
</DatabaseSchema>

