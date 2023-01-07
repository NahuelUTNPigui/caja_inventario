<script>
  import Home from './Home.svelte'
  import Navegacion from './Navegacion.svelte';
  import ListaClientes from './clientes/list.svelte'
  import DetalleCliente from './clientes/detail.svelte'
  import ListaCompras from './compras/list.svelte'
  import DetalleCompra from './compras/detail.svelte'
  import ListaEgresos from './egresos/list.svelte'
  import DetalleEgreso from './egresos/detail.svelte'
  import ListaIngresos from './ingresos/list.svelte'
  import DetalleIngreso from './ingresos/detail.svelte'
  import ListaProductos from './productos/list.svelte'
  import DetalleProducto from './productos/detail.svelte'
  import ListaProveedores from './proveedores/list.svelte'
  import DetalleProveedor from './proveedores/list.svelte'
  import Reportes from './reportes/reporte.svelte'
  import ListaVentas from './ventas/list.svelte'
  import DetalleVenta from './ventas/detail.svelte'

  import {Router,Route} from "svelte-routing"
    import Reporte from './reportes/reporte.svelte';

  export let url = ""
  let nombre =" nahuel"
</script>

<main>
  Caja inventario {nombre}
  <Navegacion></Navegacion>
  <br>
  <br>
  <Router url="{url}">
    <Route path="/">
      <Home></Home>
    </Route>
    <Route path="/clientes">
      <ListaClientes></ListaClientes>
    </Route>
    <Route path="/detallecliente">
      <DetalleCliente></DetalleCliente>
    </Route>
    <Route path="/compras">
      <ListaCompras></ListaCompras>
    </Route>
    <Route path="/detallecompra">
      <DetalleCompra></DetalleCompra>
    </Route>
    <Route path="/egresos">
      <ListaEgresos></ListaEgresos>
    </Route>
    <Route path="/detalleegreso">
      <DetalleEgreso></DetalleEgreso>
    </Route>
    <Route path="/ingresos">
      <ListaIngresos></ListaIngresos>
    </Route>
    <Route path="/detalleingreso">
      <DetalleIngreso></DetalleIngreso>
    </Route>
    <Route path="/productos">
      <ListaProductos></ListaProductos>
    </Route>
    <Route path="/detalleproducto">
      <DetalleProducto></DetalleProducto>
    </Route>
    <Route path="/proveedores">
      <ListaProveedores></ListaProveedores>
    </Route>
    <Route path="/detalleproveedor">
      <DetalleProveedor></DetalleProveedor>>
    </Route>
    <Route path="/reportes">
      <Reporte></Reporte>
    </Route>
    <Route path="/ventas">
      <ListaVentas></ListaVentas>
    </Route>
    <Route path="/detalleventa">
      <DetalleVenta></DetalleVenta>
    </Route>    
  </Router>
</main>

