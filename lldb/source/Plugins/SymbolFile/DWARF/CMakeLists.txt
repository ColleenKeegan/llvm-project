lldb_tablegen(Properties.inc -gen-lldb-property-defs
  SOURCE Properties.td
  TARGET LLDBPluginSymbolFileDWARFPropertiesGen)

lldb_tablegen(PropertiesEnum.inc -gen-lldb-property-enum-defs
  SOURCE Properties.td
  TARGET LLDBPluginSymbolFileDWARFPropertiesEnumGen)

add_lldb_library(lldbPluginSymbolFileDWARF PLUGIN
  AppleDWARFIndex.cpp
  DebugNamesDWARFIndex.cpp
  DIERef.cpp
  DWARFAbbreviationDeclaration.cpp
  DWARFASTParserClang.cpp
  DWARFAttribute.cpp
  DWARFBaseDIE.cpp
  DWARFCompileUnit.cpp
  DWARFContext.cpp
  DWARFDataExtractor.cpp
  DWARFDebugAbbrev.cpp
  DWARFDebugAranges.cpp
  DWARFDebugArangeSet.cpp
  DWARFDebugInfo.cpp
  DWARFDebugInfoEntry.cpp
  DWARFDebugLine.cpp
  DWARFDebugMacro.cpp
  DWARFDebugRanges.cpp
  DWARFDeclContext.cpp
  DWARFDefines.cpp
  DWARFDIE.cpp
  DWARFFormValue.cpp
  DWARFIndex.cpp
  DWARFTypeUnit.cpp
  DWARFUnit.cpp
  HashedNameToDIE.cpp
  LogChannelDWARF.cpp
  ManualDWARFIndex.cpp
  NameToDIE.cpp
  SymbolFileDWARF.cpp
  SymbolFileDWARFDwo.cpp
  SymbolFileDWARFDwoDwp.cpp
  SymbolFileDWARFDwp.cpp
  SymbolFileDWARFDebugMap.cpp
  UniqueDWARFASTType.cpp

  LINK_LIBS
    clangAST
    clangBasic
    lldbCore
    lldbExpression
    lldbHost
    lldbInterpreter
    lldbSymbol
    lldbTarget
    lldbUtility
    lldbPluginObjCLanguage
    lldbPluginCPlusPlusLanguage
    lldbPluginExpressionParserClang
  LINK_COMPONENTS
    DebugInfoDWARF
    Support
  )

add_dependencies(lldbPluginSymbolFileDWARF
  LLDBPluginSymbolFileDWARFPropertiesGen
  LLDBPluginSymbolFileDWARFPropertiesEnumGen)
