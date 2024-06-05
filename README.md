"#SISTEMA DE COMPRA E VENDAS DE GADO" 

CREATE TABLE FORNECEDOR (
  FORNECOD BIGINT NOT NULL PRIMARY KEY,
  FORNENOME VARCHAR(200) NOT NULL,
  FORNEENDERECO VARCHAR(300) NOT NULL,
  FORNETELEFONE VARCHAR(14) NOT NULL,
  FORNECPF CHAR(11) NOT NULL
);

CREATE TABLE GADO (
  GADCOD BIGINT NOT NULL PRIMARY KEY,
  GADRACA VARCHAR(150) NOT NULL,
  GADSEXO CHAR(1) NOT NULL,
  GADIDADE VARCHAR(20) NOT NULL,
  GADPESO INTEGER NOT NULL,
  FORNECOD BIGINT NOT NULL,
  FOREIGN KEY (FORNECOD) REFERENCES FORNECEDOR
);

CREATE TABLE COMPRADOR (
  COMPCOD BIGINT NOT NULL PRIMARY KEY,
  COMPNOME VARCHAR(200) NOT NULL,
  COMPENDERECO VARCHAR(300) NOT NULL,
  COMPTELEFONE VARCHAR(14) NOT NULL,
  COMPCPF CHAR(11) NOT NULL
);
CREATE TABLE PEDIDO (
  PEDICOD BIGINT NOT NULL PRIMARY KEY,
  DATA DATE NOT NULL,
  COMPCOD BIGINT NOT NULL,
  FORNECOD BIGINT NOT NULL,
  FOREIGN KEY (COMPCOD) REFERENCES COMPRADOR,
  FOREIGN KEY (FORNECOD) REFERENCES FORNECEDOR
);

CREATE TABLE NOTA_FISCAL (
  NFCOD BIGINT NOT NULL PRIMARY KEY,
  NFVALORTOTAL NUMERIC(8,2) NOT NULL,
  DATA DATE NOT NULL,
  PEDICOD BIGINT NOT NULL,
  FOREIGN KEY (PEDICOD) REFERENCES PEDIDO
);

CREATE TABLE ESTOQUE (
  ESTCOD BIGINT NOT NULL PRIMARY KEY,
  ESTQUANTIDADE INTEGER NOT NULL,
  GADCOD BIGINT NOT NULL,
  FOREIGN KEY (GADCOD) REFERENCES GADO
);
