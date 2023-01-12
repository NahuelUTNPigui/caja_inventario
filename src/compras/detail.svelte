<script>    
    import { navigate } from 'svelte-routing';
    import {Container,Row,Col,Form,Input,Label,Button,Table} from 'sveltestrap'
    import {ruta} from '../store'
    export let codCompra="0"
    let codProveedor=""
    let nombreProveedor="pedro"
    let fecha="12/11/2022"
    let monto = "100"
    let nombreProducto='papel'
    let cantidad="5"
    let precio_compra="1.5"
    let RUTA = ''
    ruta.subscribe(v=>RUTA = v)
    async function exito(e){
        e.preventDefault()
        navigate('/compras')
    }
    function cancelar(e){
        e.preventDefault()
        navigate('/compras')
    }
    let detalles_compras=[
        {nombre_producto:'papel',cantidad:5,precio:1.0}
    ]
</script>
<Container>
    <Row>
        <Col>
            <h2>Compras</h2>
            {#if codCompra == "0"}
                <p>Nueva compra</p>
            {:else}
                <p>Modificar compra</p>
            {/if}
            <Form>

                <Container>
                    <Row>
                        <Col>
                            <Label for="monto">Monto</Label>
                            <Input
                              type="text"
                              name="monto"
                              id="monto"
                              placeholder="monto"
                              bind:value="{monto}"
                            />         
                        </Col>
                    </Row>
                    <Row>
                        <Col>
                            <Label for="proveedor">Proveedor</Label>
                            <Input
                              type="text"
                              name="proveedor"
                              id="proveedor"
                              placeholder="proveedor"
                              bind:value="{nombreProveedor}"
                            />
                        </Col>
                        <Col>
                            <Label for="fecha">Fecha</Label>
                            <Input
                              type="text"
                              name="fecha"
                              id="fecha"
                              placeholder="fecha"
                              bind:value="{fecha}"
                            />
                        </Col>
                    </Row>
                    <Row>
                        <Col>
                            <Label for="nombreProducto">Producto</Label>
                            <Input
                              type="text"
                              name="nombreProducto"
                              id="nombreProducto"
                              placeholder="nombreProducto"
                              bind:value="{nombreProducto}"
                            />
                        </Col>
                        <Col>
                            <Label for="cantidad">Cantidad</Label>
                            <Input
                              type="text"
                              name="cantidad"
                              id="cantidad"
                              placeholder="cantidad"
                              bind:value="{cantidad}"
                            />
                        </Col>
                        <Col>
                            <Label for="precio_compra">Precio compra</Label>
                            <Input
                              type="text"
                              name="precio_compra"
                              id="precio_compra"
                              placeholder="precio_compra"
                              bind:value="{precio_compra}"
                            />
                        </Col>
                        <Col>
                            <br>
                            <Button>Agregar o modifcar</Button>
                        </Col>
                    </Row>
                    <Row>
                        <Col>
                            <Table>
                                <thead>
                                    <tr>
                                        <th>Nombre</th>
                                        <th>Cantidad</th>
                                        <th>Precio</th>
                                        <th>Acciones</th>
                                        <th></th>
                                    </tr>
                                </thead>
                                <tbody>
                                    {#each detalles_compras as dc}
                                        <tr>
                                            <td>{dc.nombre_producto}</td>
                                            <td>{dc.cantidad}</td>
                                            <td>{dc.precios}</td>
                                            <td><Button>Modificar</Button></td>
                                            <td><Button>Eliminar</Button></td>
                                        </tr>
                                    {/each}
                                    <tr></tr>
                                </tbody>
                            </Table>
                        </Col>
                    </Row>
                    <Row>
                            
                        <Col>
                            <br>
                            <Button outline color="success" on:click={exito}>Guardar</Button>
                        </Col>
                        <Col>
                            <br>
                            <Button outline color="danger" on:click={cancelar}>cancelar</Button>
                        </Col>
                    </Row>
                </Container>
            </Form>
        </Col>
    </Row>
</Container>