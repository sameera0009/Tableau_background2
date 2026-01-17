import React, { useEffect, useRef } from 'react';

const GlassDashboard = () => {
  const canvasRef = useRef(null);

  useEffect(() => {
    const canvas = canvasRef.current;
    const ctx = canvas.getContext('2d');
    let animationFrameId;
    let time = 0;

    const resizeCanvas = () => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    };

    resizeCanvas();
    window.addEventListener('resize', resizeCanvas);

    const drawBackground = () => {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      
      const gradient = ctx.createRadialGradient(
        canvas.width * 0.5, canvas.height * 0.3, 0,
        canvas.width * 0.5, canvas.height * 0.5, canvas.width * 0.8
      );
      gradient.addColorStop(0, '#0ea5e9');
      gradient.addColorStop(0.4, '#0284c7');
      gradient.addColorStop(0.7, '#0369a1');
      gradient.addColorStop(1, '#075985');
      ctx.fillStyle = gradient;
      ctx.fillRect(0, 0, canvas.width, canvas.height);

      ctx.save();
      for (let i = 0; i < 8; i++) {
        ctx.beginPath();
        
        for (let x = 0; x < canvas.width; x += 2) {
          const y = canvas.height * (0.2 + i * 0.1) + 
            Math.sin((x * 0.002) + (time * 0.008) + (i * 0.7)) * 25 +
            Math.cos((x * 0.0015) + (time * 0.005) + (i * 0.4)) * 18;
          
          if (x === 0) {
            ctx.moveTo(x, y);
          } else {
            ctx.lineTo(x, y);
          }
        }

        ctx.strokeStyle = `rgba(255, 255, 255, ${0.05 + Math.sin(time * 0.02 + i) * 0.02})`;
        ctx.lineWidth = 1.5;
        ctx.stroke();
      }
      ctx.restore();

      time += 1;
      animationFrameId = requestAnimationFrame(drawBackground);
    };

    drawBackground();

    return () => {
      window.removeEventListener('resize', resizeCanvas);
      cancelAnimationFrame(animationFrameId);
    };
  }, []);

  const cards = [
    { width: 'col-span-2', height: 'row-span-2' },
    { width: 'col-span-1', height: 'row-span-1' },
    { width: 'col-span-1', height: 'row-span-1' },
    { width: 'col-span-1', height: 'row-span-2' },
    { width: 'col-span-2', height: 'row-span-1' },
    { width: 'col-span-1', height: 'row-span-1' }
  ];

  return (
    <div className="relative w-full h-screen overflow-hidden flex flex-col">
      <canvas
        ref={canvasRef}
        className="absolute inset-0 w-full h-full"
      />
      
      {/* Header Bar */}
      <header className="relative z-20 backdrop-blur-2xl bg-gradient-to-r from-white/20 via-white/15 to-white/20 border-b border-white/30 shadow-lg">
        <div className="h-20 px-8 flex items-center" style={{ boxShadow: 'inset 0 1px 0 rgba(255, 255, 255, 0.3)' }}>
          <div className="absolute inset-0 bg-gradient-to-b from-white/10 to-transparent pointer-events-none" />
          <div className="relative flex items-center gap-3">
            <div className="w-10 h-10 rounded-xl bg-white/30 backdrop-blur-sm border border-white/40 flex items-center justify-center">
              <div className="w-6 h-6 rounded-lg bg-gradient-to-br from-cyan-400 to-blue-600" />
            </div>
          </div>
        </div>
      </header>

      {/* Main Content */}
      <div className="relative z-10 flex-1 overflow-auto">
        <div className="min-h-full p-8 flex items-center justify-center">
          <div className="w-full max-w-[1600px]">
            <div className="grid grid-cols-4 grid-rows-3 gap-6 auto-rows-[200px]">
              {cards.map((card, index) => (
                <div
                  key={index}
                  className={`group relative ${card.width} ${card.height}`}
                  style={{
                    animation: `slideIn 1s cubic-bezier(0.16, 1, 0.3, 1) ${index * 0.1}s both`
                  }}
                >
                  <div 
                    className="absolute -inset-1 bg-gradient-to-br from-sky-400/40 via-blue-500/30 to-cyan-400/40 rounded-[2rem] blur-xl opacity-0 group-hover:opacity-100 transition-all duration-700"
                    style={{
                      animation: 'breathe 4s ease-in-out infinite'
                    }}
                  />
                  
                  <div 
                    className="relative w-full h-full backdrop-blur-2xl bg-gradient-to-br from-white/25 via-white/15 to-white/5 rounded-[1.75rem] shadow-[0_8px_32px_rgba(0,0,0,0.12)] border border-white/30 overflow-hidden transition-all duration-500 hover:border-white/50"
                    style={{
                      boxShadow: '0 8px 32px rgba(14, 165, 233, 0.15), inset 0 1px 0 rgba(255, 255, 255, 0.3)'
                    }}
                  >
                    <div className="absolute top-0 left-0 right-0 h-1/2 bg-gradient-to-b from-white/20 to-transparent opacity-60" />
                    
                    <div 
                      className="absolute inset-0 opacity-0 group-hover:opacity-100 transition-opacity duration-1000"
                      style={{
                        background: 'radial-gradient(circle at 50% 0%, rgba(125, 211, 252, 0.2) 0%, transparent 60%)',
                        animation: 'drift 8s ease-in-out infinite'
                      }}
                    />
                    
                    <div 
                      className="absolute w-20 h-20 rounded-full bg-blue-200/20 blur-xl"
                      style={{
                        animation: `gentle-float-1 7s ease-in-out infinite ${index * 0.3}s`,
                        top: '30%',
                        left: '25%'
                      }}
                    />
                    <div 
                      className="absolute w-16 h-16 rounded-full bg-cyan-200/15 blur-xl"
                      style={{
                        animation: `gentle-float-2 9s ease-in-out infinite ${index * 0.5}s`,
                        bottom: '30%',
                        right: '25%'
                      }}
                    />
                    <div 
                      className="absolute w-12 h-12 rounded-full bg-sky-300/20 blur-lg"
                      style={{
                        animation: `gentle-float-3 6s ease-in-out infinite ${index * 0.4}s`,
                        top: '50%',
                        right: '35%'
                      }}
                    />
                    
                    <div 
                      className="absolute inset-0 opacity-0 group-hover:opacity-100"
                      style={{
                        background: 'linear-gradient(to bottom, transparent 0%, rgba(255,255,255,0.05) 50%, transparent 100%)',
                        animation: 'scan 3s ease-in-out infinite'
                      }}
                    />
                    
                    <div className="absolute top-4 left-4 w-12 h-12 border-t-2 border-l-2 border-white/40 rounded-tl-xl opacity-60 group-hover:opacity-100 transition-opacity duration-500" />
                    <div className="absolute bottom-4 right-4 w-12 h-12 border-b-2 border-r-2 border-white/40 rounded-br-xl opacity-60 group-hover:opacity-100 transition-opacity duration-500" />
                  </div>
                </div>
              ))}
            </div>
          </div>
        </div>
      </div>

      {/* Footer Bar */}
      <footer className="relative z-20 backdrop-blur-2xl bg-gradient-to-r from-white/20 via-white/15 to-white/20 border-t border-white/30 shadow-lg">
        <div className="h-16 px-8 flex items-center justify-center" style={{ boxShadow: 'inset 0 -1px 0 rgba(255, 255, 255, 0.3)' }}>
          <div className="absolute inset-0 bg-gradient-to-t from-white/10 to-transparent pointer-events-none" />
          <div className="relative flex gap-2">
            {[...Array(5)].map((_, i) => (
              <div 
                key={i} 
                className="w-2 h-2 rounded-full bg-white/40"
                style={{
                  animation: `pulse-dot 2s ease-in-out infinite ${i * 0.2}s`
                }}
              />
            ))}
          </div>
        </div>
      </footer>

      <style jsx>{`
        @keyframes slideIn {
          from {
            opacity: 0;
            transform: translateY(30px);
          }
          to {
            opacity: 1;
            transform: translateY(0);
          }
        }
        
        @keyframes breathe {
          0%, 100% {
            opacity: 0;
            transform: scale(0.95);
          }
          50% {
            opacity: 1;
            transform: scale(1.02);
          }
        }
        
        @keyframes drift {
          0%, 100% {
            transform: translateY(0) scale(1);
          }
          50% {
            transform: translateY(-10px) scale(1.05);
          }
        }
        
        @keyframes gentle-float-1 {
          0%, 100% {
            transform: translate(0, 0);
          }
          25% {
            transform: translate(8px, -6px);
          }
          50% {
            transform: translate(-4px, -10px);
          }
          75% {
            transform: translate(-8px, -4px);
          }
        }
        
        @keyframes gentle-float-2 {
          0%, 100% {
            transform: translate(0, 0);
          }
          33% {
            transform: translate(-10px, 8px);
          }
          66% {
            transform: translate(6px, -6px);
          }
        }
        
        @keyframes gentle-float-3 {
          0%, 100% {
            transform: translate(0, 0) scale(1);
          }
          50% {
            transform: translate(-8px, 10px) scale(1.1);
          }
        }
        
        @keyframes scan {
          0% {
            transform: translateY(-100%);
          }
          100% {
            transform: translateY(100%);
          }
        }
        
        @keyframes pulse-dot {
          0%, 100% {
            opacity: 0.4;
            transform: scale(1);
          }
          50% {
            opacity: 1;
            transform: scale(1.3);
          }
        }
      `}</style>
    </div>
  );
};

export default GlassDashboard;
