---
name: skill-3d-porsche-animation
description: Lógica de animação e renderização 3D de alta fidelidade para o Porsche 911 usando React Three Fiber. Use esta skill para configurar cenas 3D automotivas com iluminação de estúdio e efeitos de flutuação.
---

# 🏎️ Skill: 3D Porsche Animation (Nexus Edition)

Esta skill documenta o padrão de implementação para visualizadores 3D de alta fidelidade no ecossistema Alavanca AI.

## 🛠️ Stack Recomendada
- `@react-three/fiber` (Core)
- `@react-three/drei` (Helpers: Float, Environment, ContactShadows)
- `three` (Engine)

## 📐 Configuração da Cena (Studio Lighting)

Para um visual "Chiaroscuro" (estilo Ferrari), use a seguinte configuração no componente `Scene.jsx`:

```jsx
<Canvas shadows camera={{ position: [5, 2, 5], fov: 35 }}>
  <color attach="background" args={['#09090b']} />
  
  {/* Iluminação de Estúdio */}
  <Environment preset="city" />
  <SpotLight position={[10, 10, 10]} angle={0.15} penumbra={1} intensity={2} castShadow />
  
  {/* Sombras de Contato Realistas */}
  <ContactShadows 
    position={[0, -0.8, 0]} 
    opacity={0.65} 
    scale={10} 
    blur={2.5} 
    far={1} 
  />
  
  {/* Modelo com Efeito Antigravity */}
  <Float speed={1.5} rotationIntensity={0.5} floatIntensity={0.5}>
    <Porsche scale={0.015} />
  </Float>
  
  <OrbitControls enableZoom={false} autoRotate autoRotateSpeed={0.5} />
</Canvas>
```

## 🚗 Carregamento do Asset (`Porsche.jsx`)

Sempre utilize o objeto `scene` diretamente para garantir que materiais e geometrias complexas sejam renderizados corretamente.

```jsx
import { useGLTF } from '@react-three/drei';

export function Porsche(props) {
  const { scene } = useGLTF('/models/free_porsche_911_carrera_4s.glb');
  
  // Otimização: Traverse para sombras se necessário
  scene.traverse((child) => {
    if (child.isMesh) {
      child.castShadow = true;
      child.receiveShadow = true;
    }
  });

  return <primitive object={scene} {...props} />;
}
```

## 🎯 Regras de Ouro
1. **Escala:** Carros GLB costumam vir em escalas gigantescas. Use `scale={0.015}` ou similar para caber no viewport.
2. **Performance:** Sempre faça o preload do modelo: `useGLTF.preload('/path/to/model.glb')`.
3. **Interatividade:** Use `autoRotate` sutil para manter a cena viva ("Antigravity effect").
