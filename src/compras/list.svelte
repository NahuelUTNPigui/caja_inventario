<script>
    import { Link, navigate, Router } from 'svelte-routing';
    import {Container,Row,Col,Button,Table,Input,Modal,ModalBody,ModalFooter,ModalHeader} from 'sveltestrap'
    import {ruta} from '../store'
    let RUTA = ''
    ruta.subscribe(v=>RUTA = v)
    export let url=""
    let proveedor = ""
    let fecha = ""
    let monto = ""
    let open = false
    const toggle = ()=>{open = !open}
    function nuevo_compra(){
        navigate('/detallecompra')
    }
    async function eliminarCompra(){

        toggle()
    }
    let compras = [{nombre_proveedor:"nahuel",fecha:'20/11/2022',monto:'1231'},]

</script>
<div>
    <Modal isOpen={open} {toggle}>
      <ModalHeader {toggle}>Eliminar compra</ModalHeader>
      <ModalBody>
        Esta seguro que desea eliminar la compra?.
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
                    <Col><Button on:click={nuevo_compra}>Nuevo compra</Button></Col>
                    <Col name="nombre">Proveedor</Col>
                    <Col><Input
                        type="text"
                        name="nombre"
                        id="nombre"
                        bind:value="{proveedor}"
                    /></Col>
                    <Col name="fecha">fecha</Col>
                    <Col><Input
                        type="text"
                        name="fecha"
                        id="fecha"
                        bind:value="{fecha}"
                    /></Col>
                    <Col><Button>Buscar</Button></Col>

                </Row>
            </Container>
            <hr>
            <Table>
                <thead>
                    <tr>
                        <th>Proveedor</th>
                        <th>Fecha</th>
                        <th>Monto</th>
                        <th>Acciones</th>
                        <th></th>
                    </tr>
                </thead>
                <tbody>
                    {#each compras as c}
                    <tr>
                        <td>{c.nombre_proveedor}</td>
                        <td>{c.fecha}</td>
                        <td>{c.monto}</td>
                        <td>
                            <Router url="{url}">
                                <nav>
                                    <Link to="/detallecompra">Modificar</Link>
                                </nav>
                            </Router>    
                        <td>
                        <td><Button outline color='danger' on:click={()=>eliminarCompra()}>Eliminar</Button></td>
                    </tr>
                    {/each}
                </tbody>
            </Table>
        </Col>
    </Row>
</Container>
