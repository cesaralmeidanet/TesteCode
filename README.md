# TesteCode
> Pesquisa Sistema de Vendas
> Pesquisa informações sobre Clientes, Produtos e Funcionário sem movimentação.
> Pesquisa vendas por Marca consolidado por Loja.
> Liguagem: SQL
> Banco de Dados: SQL Server



> Listar todos os clientes que nao realizaram uma compra;
  Select cm.*
  from   customers as cm
  left join orders as od
  on  cm.customer_id = od.customer_id
  where  od.order_id is null

> Listar os produtos que não tenham sido comprados;
  Select pr.*
  from  products as pr
  left join orders as od
  on pr.product_id = od.product_id
  where od.order_id is null

> Listar os produtos sem estoque;
  Select st.*
  from stocks as st
  where st.quantity = 0

> Agrupar a quantidade de vendas de uma determinada marca por loja;
  Select br.name, st.store_name, sum(it.quantity)
  from   brands as br
  inner join product_id as pr
  on  br.brand_id = pr.brand_id
  inner join order_itens as it
  on  pr.product_id = it.product_id
  inner join orders as od
  on  od.order_id = it.order_id
  inner join stores as st
  on  st.store_id = od.store_id
  group  by br.name, st.name

> Listar os funcionários que não estejam relacionados a um pedido;
  Select sf.*
  from  staffs as sf
  left join orders as od
  on  sf.staff_id = od.staff_id
  where od.staff_id is null

> This is a challenge by [Coodesh](https://coodesh.com/)
  

  
