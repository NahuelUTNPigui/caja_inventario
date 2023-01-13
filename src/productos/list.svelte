<script>
    import { Link, navigate, Router } from 'svelte-routing';
    import {Container,Row,Col,Button,Table,Input,Modal,ModalBody,ModalFooter,ModalHeader} from 'sveltestrap'
    import {ruta} from '../store'
    let RUTA = ''
    ruta.subscribe(v=>RUTA = v)
    export let url=""
    let nombre = ""
    let precio_venta=""
    let cantidad = ""
    let open = false
    const toggle = ()=>{open = !open}
    function nuevo_producto(){
        navigate('/detalleproducto')
    }
    async function eliminarProducto(){

        toggle()
    }
    let productos = [{nombre:"nahuel",precio_venta:'555',cantidad:'15'},]
</script>
<div>
    <Modal isOpen={open} {toggle}>
      <ModalHeader {toggle}>Eliminar producto</ModalHeader>
      <ModalBody>
        Esta seguro que desea eliminar el producto?.
        <br>
        Podria modificar informacion en el stock y la caja
      </ModalBody>
      <ModalFooter>
        <Button color="danger">Eliminar</Button>
        <Button color="secondary">Cancel</Button>
      </ModalFooter>
    </Modal>
</div>
<Container>
  <Row>
      <Col>
          <Container>
              <Row>
                  <Col><Button on:click={nuevo_producto}>Nuevo producto</Button></Col>
                  <Col name="nombre">Producto</Col>
                  <Col><Input
                      type="text"
                      name="nombre"
                      id="nombre"
                      bind:value="{nombre}"
                  /></Col>
                  <Col name="cantidad">Cantidad</Col>
                  <Col><Input
                      type="text"
                      name="cantidad"
                      id="cantidad"
                      bind:value="{cantidad}"
                  /></Col>
                  <Col><Button>Buscar</Button></Col>

              </Row>
          </Container>
          <hr>
          <Table>
              <thead>
                  <tr>
                      <th>Producto</th>
                      <th>Cantidad</th>
                      <th>Precio Venta</th>
                      <th>Acciones</th>
                      <th></th>
                  </tr>
              </thead>
              <tbody>
                  {#each productos as p}
                  <tr>
                      <td>{p.nombre}</td>
                      <td>{p.cantidad}</td>
                      <td>{p.precio_venta}</td>
                      <td>
                          <Router url="{url}">
                              <nav>
                                  <Link to="/detalleproducto">Modificar</Link>
                              </nav>
                          </Router>    
                      <td>
                      <td><Button outline color='danger' on:click={()=>eliminarProducto()}>Eliminar</Button></td>
                  </tr>
                  {/each}
              </tbody>
          </Table>
      </Col>
  </Row>
</Container>