<script setup lang="ts">
import { ref } from 'vue'
import Button from '@/components/ui/Button.vue'
import Card from '@/components/ui/Card.vue'
import CardHeader from '@/components/ui/CardHeader.vue'
import CardTitle from '@/components/ui/CardTitle.vue'
import CardDescription from '@/components/ui/CardDescription.vue'
import CardContent from '@/components/ui/CardContent.vue'
import Badge from '@/components/ui/Badge.vue'
import { useIntersectionObserver } from '@/composables/useIntersectionObserver'
import { Code2, Sparkles, Target, Heart } from 'lucide-vue-next'

const cardRef = ref<HTMLElement | null>(null)
const { isInView } = useIntersectionObserver(cardRef, { threshold: 0.1, triggerOnce: true })
</script>

<template>
  <div class="min-h-screen bg-background p-8">
    <div class="container mx-auto max-w-6xl">
      <div class="text-center mb-12">
        <h1 class="text-5xl font-bold mb-4 text-foreground animate-fade-in-up">
          UI Components Showcase
        </h1>
        <p class="text-lg text-muted-foreground">
          Design System baseado no projeto React
        </p>
      </div>

      <div class="space-y-12">
        <!-- Buttons Section -->
        <section class="bg-card p-8 rounded-lg border">
          <h2 class="text-3xl font-bold mb-6 flex items-center gap-2">
            <Code2 class="w-8 h-8 text-accent" />
            Buttons
          </h2>
          
          <div class="space-y-6">
            <div>
              <h3 class="text-sm font-semibold text-muted-foreground mb-3">Variantes</h3>
              <div class="flex flex-wrap gap-4">
                <Button>Default</Button>
                <Button variant="secondary">Secondary</Button>
                <Button variant="outline">Outline</Button>
                <Button variant="ghost">Ghost</Button>
                <Button variant="destructive">Destructive</Button>
                <Button variant="link">Link</Button>
              </div>
            </div>

            <div>
              <h3 class="text-sm font-semibold text-muted-foreground mb-3">Tamanhos</h3>
              <div class="flex flex-wrap items-center gap-4">
                <Button size="sm">Small</Button>
                <Button size="default">Default</Button>
                <Button size="lg">Large</Button>
                <Button size="icon">
                  <Heart />
                </Button>
              </div>
            </div>

            <div>
              <h3 class="text-sm font-semibold text-muted-foreground mb-3">Com Classes Customizadas</h3>
              <div class="flex flex-wrap gap-4">
                <Button class="gradient-accent text-accent-foreground shadow-elegant">
                  Gradient Button
                </Button>
                <Button variant="outline" class="border-2 border-accent text-accent hover:bg-accent hover:text-accent-foreground">
                  Custom Outline
                </Button>
              </div>
            </div>
          </div>
        </section>

        <!-- Badges Section -->
        <section class="bg-card p-8 rounded-lg border">
          <h2 class="text-3xl font-bold mb-6 flex items-center gap-2">
            <Sparkles class="w-8 h-8 text-accent" />
            Badges
          </h2>
          
          <div class="space-y-4">
            <div>
              <h3 class="text-sm font-semibold text-muted-foreground mb-3">Variantes</h3>
              <div class="flex flex-wrap gap-2">
                <Badge>Default</Badge>
                <Badge variant="secondary">Secondary</Badge>
                <Badge variant="outline">Outline</Badge>
                <Badge variant="destructive">Destructive</Badge>
              </div>
            </div>

            <div>
              <h3 class="text-sm font-semibold text-muted-foreground mb-3">Exemplo de Uso (Stack de Tecnologias)</h3>
              <div class="flex flex-wrap gap-2">
                <Badge variant="secondary">Vue 3</Badge>
                <Badge variant="secondary">TypeScript</Badge>
                <Badge variant="secondary">Tailwind CSS</Badge>
                <Badge variant="secondary">Vite</Badge>
                <Badge variant="secondary">Pinia</Badge>
              </div>
            </div>
          </div>
        </section>

        <!-- Cards Section -->
        <section class="space-y-6">
          <h2 class="text-3xl font-bold flex items-center gap-2">
            <Target class="w-8 h-8 text-accent" />
            Cards
          </h2>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <!-- Card Básico -->
            <Card>
              <CardHeader>
                <CardTitle>Card Básico</CardTitle>
                <CardDescription>Exemplo de card com header e content</CardDescription>
              </CardHeader>
              <CardContent>
                <p class="text-muted-foreground">
                  Este é um card simples usando os componentes Card, CardHeader, CardTitle, 
                  CardDescription e CardContent.
                </p>
              </CardContent>
            </Card>

            <!-- Card com Ícone -->
            <Card class="p-8 hover:shadow-lg transition-smooth border-l-4 border-accent">
              <div class="flex items-center gap-4 mb-4">
                <div class="p-3 rounded-lg bg-accent/10">
                  <Sparkles class="w-6 h-6 text-accent" />
                </div>
                <h3 class="text-xl font-bold text-card-foreground">Card com Ícone</h3>
              </div>
              <p class="text-muted-foreground mb-4">
                Card customizado com borda lateral, ícone e hover effect.
              </p>
              <div class="flex gap-2">
                <Badge variant="secondary">Feature</Badge>
                <Badge variant="secondary">Design</Badge>
              </div>
            </Card>

            <!-- Card de Projeto -->
            <Card class="p-8 hover:shadow-lg transition-smooth group">
              <div class="mb-4">
                <Code2 class="w-10 h-10 text-accent mb-4" />
                <h3 class="text-2xl font-bold mb-4 text-card-foreground group-hover:text-accent transition-smooth">
                  Card de Projeto
                </h3>
              </div>
              <p class="text-muted-foreground mb-4 leading-relaxed">
                Este card demonstra um estilo que poderia ser usado para exibir projetos no portfolio.
              </p>
              <div class="flex items-start gap-2 mb-6 p-4 bg-accent/5 rounded-lg border border-accent/20">
                <Target class="w-5 h-5 text-accent flex-shrink-0 mt-0.5" />
                <p class="text-sm text-card-foreground font-medium">
                  Impacto: Aumentou eficiência em 40%
                </p>
              </div>
              <div class="flex flex-wrap gap-2">
                <Badge variant="secondary">React</Badge>
                <Badge variant="secondary">Node.js</Badge>
                <Badge variant="secondary">MongoDB</Badge>
              </div>
            </Card>

            <!-- Card de Experiência -->
            <Card class="p-8 border-l-4 border-accent bg-card hover:shadow-lg transition-smooth">
              <div class="flex items-start gap-4 mb-4">
                <div class="p-3 rounded-lg bg-accent/10 flex-shrink-0">
                  <Code2 class="w-6 h-6 text-accent" />
                </div>
                <div class="flex-1">
                  <h3 class="text-2xl font-bold text-card-foreground mb-1">
                    Senior Developer
                  </h3>
                  <p class="text-accent font-semibold mb-1">Empresa XYZ</p>
                  <p class="text-sm text-muted-foreground">2020 - Presente</p>
                </div>
              </div>
              <ul class="space-y-2 text-muted-foreground">
                <li class="flex items-start gap-2">
                  <span class="text-accent mt-1">•</span>
                  <span>Desenvolveu aplicações Vue.js de alta performance</span>
                </li>
                <li class="flex items-start gap-2">
                  <span class="text-accent mt-1">•</span>
                  <span>Liderou equipe de 5 desenvolvedores</span>
                </li>
              </ul>
            </Card>
          </div>
        </section>

        <!-- Scroll Animation Section -->
        <section class="space-y-6">
          <h2 class="text-3xl font-bold">Animações de Scroll</h2>
          <p class="text-muted-foreground">Role a página para ver este card aparecer com animação</p>
          
          <Card
            ref="cardRef"
            :class="[
              'p-8 transition-all duration-700',
              isInView ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-10'
            ]"
          >
            <div class="flex items-center gap-4 mb-4">
              <Target class="w-8 h-8 text-accent" />
              <h3 class="text-2xl font-bold">Animated on Scroll</h3>
            </div>
            <p class="text-muted-foreground">
              Este card aparece com uma animação suave quando entra no viewport usando o 
              composable useIntersectionObserver!
            </p>
          </Card>
        </section>

        <!-- Gradients & Styles Section -->
        <section class="bg-card p-8 rounded-lg border">
          <h2 class="text-3xl font-bold mb-6">Gradientes & Estilos Customizados</h2>
          
          <div class="space-y-6">
            <div>
              <h3 class="text-sm font-semibold text-muted-foreground mb-3">Gradient Accent</h3>
              <div class="gradient-accent h-32 rounded-lg flex items-center justify-center text-accent-foreground font-bold text-xl">
                Gradient Accent
              </div>
            </div>

            <div>
              <h3 class="text-sm font-semibold text-muted-foreground mb-3">Gradient Hero (com opacity)</h3>
              <div class="gradient-hero opacity-20 h-32 rounded-lg"></div>
            </div>

            <div>
              <h3 class="text-sm font-semibold text-muted-foreground mb-3">Shadow Elegant</h3>
              <div class="bg-card border rounded-lg p-6 shadow-elegant">
                <p class="text-card-foreground">Card com shadow-elegant aplicada</p>
              </div>
            </div>
          </div>
        </section>

        <!-- Color Palette -->
        <section class="bg-card p-8 rounded-lg border">
          <h2 class="text-3xl font-bold mb-6">Paleta de Cores (Design System)</h2>
          
          <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
            <div>
              <div class="bg-primary h-20 rounded-lg mb-2"></div>
              <p class="text-sm font-semibold">Primary</p>
              <p class="text-xs text-muted-foreground">hsl(215 50% 20%)</p>
            </div>
            <div>
              <div class="bg-accent h-20 rounded-lg mb-2"></div>
              <p class="text-sm font-semibold">Accent</p>
              <p class="text-xs text-muted-foreground">hsl(185 85% 45%)</p>
            </div>
            <div>
              <div class="bg-secondary h-20 rounded-lg mb-2"></div>
              <p class="text-sm font-semibold">Secondary</p>
              <p class="text-xs text-muted-foreground">hsl(210 40% 96%)</p>
            </div>
            <div>
              <div class="bg-muted h-20 rounded-lg mb-2"></div>
              <p class="text-sm font-semibold">Muted</p>
              <p class="text-xs text-muted-foreground">hsl(210 40% 96%)</p>
            </div>
          </div>
        </section>

        <div class="text-center py-12">
          <p class="text-muted-foreground">
            Todos os componentes estão prontos para uso no portfolio! 🎉
          </p>
        </div>
      </div>
    </div>
  </div>
</template>
