<script>
    import { Link, navigate, Router } from 'svelte-routing';
    import {Container,Row,Col,Button,Table,Input,Modal,ModalBody,ModalFooter,ModalHeader} from 'sveltestrap'
    import {ruta} from '../store'
    let RUTA = ''
    ruta.subscribe(v=>RUTA = v)
    export let url=""
    let nombre = ""
    let proveedor=""
    let fecha = ""
    let open = false
    const toggle = ()=>{open = !open}
    function nuevo_egreso(){
        navigate('/detalleegreso')
    }
    async function elimineEgreso(){

        toggle()
    }
    let egresos = [{proveedor:"nahuel",monto:'555',fecha:'12/05/2022'},]
</script>
<div>
    <Modal isOpen={open} {toggle}>
      <ModalHeader {toggle}>Eliminar egreso</ModalHeader>
      <ModalBody>
        Esta seguro que desea eliminar el egreso?.
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
                    <Col><Button on:click={nuevo_egreso}>Nuevo egreso</Button></Col>
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
                    {#each egresos as e}
                    <tr>
                        <td>{e.proveedor}</td>
                        <td>{e.fecha}</td>
                        <td>{e.monto}</td>
                        <td>
                            <Router url="{url}">
                                <nav>
                                    <Link to="/detalleegreso">Modificar</Link>
                                </nav>
                            </Router>    
                        <td>
                        <td><Button outline color='danger' on:click={()=>elimineEgreso()}>Eliminar</Button></td>
                    </tr>
                    {/each}
                </tbody>
            </Table>
        </Col>
    </Row>
</Container>