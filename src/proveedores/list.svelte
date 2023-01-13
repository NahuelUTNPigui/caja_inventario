<script>
    import { Link, navigate, Router } from 'svelte-routing';
    import {Container,Row,Col,Button,Table,Input,Modal,ModalBody,ModalFooter,ModalHeader} from 'sveltestrap'
    import {ruta} from '../store'
    let RUTA = ''
    ruta.subscribe(v=>RUTA = v)
    export let url=""
    let nombre = ""
    let apellido=""
    let email=""
    let telefono=""
    let open = false
    const toggle = ()=>{open = !open}
    function nuevo_proveedor(){
        navigate('/detalleproveedor')
    }
    async function eliminarProveedor(){

        toggle()
    }
    let proveedores = [{nombre:"nahuel",apellido:'555',telefono:'15',email:"a@n"}]
</script>
<div>
    <Modal isOpen={open} {toggle}>
      <ModalHeader {toggle}>Eliminar proveedor</ModalHeader>
      <ModalBody>
        Esta seguro que desea eliminar el proveedor?.
        <br>
        Podria modificar informacion en el stock y la caja
      </ModalBody>
      <ModalFooter>
        <Button color="danger">Eliminar</Button>
        <Button color="secondary">Cancel</Button>
      </ModalFooter>
    </Modal>
</div>
lista proveedores
<Container>
    <Row>
        <Col>
            <Container>
                <Row>
                    <Col><Button on:click={nuevo_proveedor}>Nuevo proveedor</Button></Col>
                    <Col name="nombre">Proveedor</Col>
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
                    {#each proveedores as p}
                    <tr>
                        <td>{p.nombre}</td>
                        <td>{p.apellido}</td>
                        <td>{p.telefono}</td>
                        <td>{p.email}</td>
                        <td>
                            <Router url="{url}">
                                <nav>
                                    <Link to="/detalleproveedor">Modificar</Link>
                                </nav>
                            </Router>    
                        <td>
                        <td><Button outline color='danger' on:click={()=>eliminarProveedor()}>Eliminar</Button></td>
                    </tr>
                    {/each}
                </tbody>
            </Table>
        </Col>
    </Row>
  </Container>
