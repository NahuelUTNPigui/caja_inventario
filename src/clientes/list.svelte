<script>
    import { Link, navigate, Router } from 'svelte-routing';
    import {Container,Row,Col,Button,Table,Input,Modal,ModalBody,ModalFooter,ModalHeader} from 'sveltestrap'
    import {ruta} from '../store'
    let RUTA = ''
    ruta.subscribe(v=>RUTA = v)
    export let url=""
    let nombre = ""
    let open = false
    const toggle = ()=>{open = !open}
    function nuevo_cliente(){
        navigate('/detallecliente')
    }
    async function eliminarCliente(){

        toggle()
    }
    let clientes = [{nombre:"nahuel",apellido:'pigui',telefono:'1231',email:'a@n'},]
</script>
<main>
    lista clientes
    <div>
        <Modal isOpen={open} {toggle}>
          <ModalHeader {toggle}>Eliminar cliente</ModalHeader>
          <ModalBody>
            Esta seguro que desea eliminar el cliente?.
            <br>
            Podria modificar informacion en los ingresos y las ventas
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
                        <Col><Button on:click={nuevo_cliente}>Nuevo cliente</Button></Col>
                        <Col name="nombre">Nombre</Col>
                        <Col><Input
                            type="text"
                            name="nombre"
                            id="nombre"
                            bind:value="{nombre}"
                        /></Col>
                        <Col><Button>Buscar</Button></Col>

                    </Row>
                </Container>
                <hr>
                <Table>
                    <thead>
                        <tr>
                            <th>Nombre</th>
                            <th>Apellido</th>
                            <th>Telefono</th>
                            <th>Email</th>
                            <th>Acciones</th>
                            <th></th>
                        </tr>
                    </thead>
                    <tbody>
                        {#each clientes as c}
                            <tr>
                                <td>{c.nombre}</td>
                                <td>{c.apellido}</td>
                                <td>{c.telefono}</td>
                                <td>{c.email}</td>
                                <td>
                                    <Router url="{url}">
                                        <nav>
                                            <Link to="/detallecliente">Modificar</Link>
                                        </nav>
                                    </Router>    
                                <td>
                                <td><Button outline color='danger' on:click={()=>eliminarCliente()}>Eliminar</Button></td>
                            </tr>
                        {/each}

                    </tbody>
                </Table>
            </Col>
        </Row>
    </Container>

</main>
