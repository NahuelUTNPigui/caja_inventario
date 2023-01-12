<script>
    import { Link, navigate, Router } from 'svelte-routing';
    import {Container,Row,Col,Button,Table,Input,Modal,ModalBody,ModalFooter,ModalHeader} from 'sveltestrap'
    import {ruta} from '../store'
    let RUTA = ''
    ruta.subscribe(v=>RUTA = v)
    export let url=""
    let nombre = ""
    let cliente=""
    let fecha = ""
    let open = false
    const toggle = ()=>{open = !open}
    function nuevo_ingreso(){
        navigate('/detalleingreso')
    }
    async function elimineIngreso(){

        toggle()
    }
    let ingresos = [{cliente:"nahuel",monto:'555',fecha:'12/05/2022'},]
</script>
<div>
    <Modal isOpen={open} {toggle}>
      <ModalHeader {toggle}>Eliminar ingreso</ModalHeader>
      <ModalBody>
        Esta seguro que desea eliminar el ingreso?.
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
                    <Col><Button on:click={nuevo_ingreso}>Nuevo ingreso</Button></Col>
                    <Col name="nombre">Cliente</Col>
                    <Col><Input
                        type="text"
                        name="nombre"
                        id="nombre"
                        bind:value="{cliente}"
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
                    {#each ingresos as i}
                    <tr>
                        <td>{i.cliente}</td>
                        <td>{i.fecha}</td>
                        <td>{i.monto}</td>
                        <td>
                            <Router url="{url}">
                                <nav>
                                    <Link to="/detalleingreso">Modificar</Link>
                                </nav>
                            </Router>    
                        <td>
                        <td><Button outline color='danger' on:click={()=>elimineIngreso()}>Eliminar</Button></td>
                    </tr>
                    {/each}
                </tbody>
            </Table>
        </Col>
    </Row>
</Container>