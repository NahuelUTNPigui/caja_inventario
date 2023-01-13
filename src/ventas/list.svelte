<script>
    import { Link, navigate, Router } from 'svelte-routing';
    import {Container,Row,Col,Button,Table,Input,Modal,ModalBody,ModalFooter,ModalHeader} from 'sveltestrap'
    import {ruta} from '../store'
    let RUTA = ''
    ruta.subscribe(v=>RUTA = v)
    export let url=""
    let nombre_cliente = ""
    let fecha=""
    let open = false
    const toggle = ()=>{open = !open}
    function nuevo_venta(){
        navigate('/detalleventa')
    }
    async function eliminarVenta(){

        toggle()
    }
    let ventas = [{nombre_cliente:"nahuel",fecha:'20/11/2022',monto:'1231'}]
</script>
<div>
    <Modal isOpen={open} {toggle}>
      <ModalHeader {toggle}>Eliminar Venta</ModalHeader>
      <ModalBody>
        Esta seguro que desea eliminar la venta?.
        <br>
        Podria modificar informacion en el stock y la caja
      </ModalBody>
      <ModalFooter>
        <Button color="danger">Eliminar</Button>
        <Button color="secondary">Cancel</Button>
      </ModalFooter>
    </Modal>
</div>
lista ventas
<Container>
    <Row>
        <Col>
            <Container>
                <Row>
                    <Col><Button on:click={nuevo_venta}>Nuevo Venta</Button></Col>
                    <Col name="nombre">Cliente</Col>
                    <Col><Input
                        type="text"
                        name="nombre"
                        id="nombre"
                        bind:value="{nombre_cliente}"
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
                    {#each ventas as v}
                    <tr>
                        <td>{v.nombre_cliente}</td>
                        <td>{v.fecha}</td>
                        <td>{v.monto}</td>
                        <td>
                            <Router url="{url}">
                                <nav>
                                    <Link to="/detalleventa">Modificar</Link>
                                </nav>
                            </Router>    
                        <td>
                        <td><Button outline color='danger' on:click={()=>eliminarVenta()}>Eliminar</Button></td>
                    </tr>
                    {/each}
                </tbody>
            </Table>
        </Col>
    </Row>
</Container>
